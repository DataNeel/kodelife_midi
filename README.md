# kodelife_midi
In the quest to integrate midi into [my generative art](instagram.com/neel_generates), I started using [KodeLife by Hexler](https://hexler.net/products/kodelife). The midi example [in their documentation](https://hexler.net/docs/kodelife-parameters-built-in) didn't work for me, but I was able to figure it out with some tinkering and with the help of some other generative artists. Hopefully this works for you! Read the code below, or download the .klproj file in this repo.


```
#ifdef GL_ES
precision mediump float;
#endif

uniform vec2 u_resolution;
uniform vec2 u_mouse;
uniform float u_time;

//In codelife, you need to click the + button by parameters, navigate to 'built-in>input', and add 'midi channel'
//At the time of writing this, the default name is midi1. I changed it to u_midi
uniform sampler2D u_midi;


//this function takes a midi offset and turns it into coordinates for the texture/sampler
//the KodeLife examples use ints, but float seemed to be required in my case
//values are divided by 32. because the midi channel resolution is 32, but texture2D requires 0.-1.
vec2 midiCoord(float offset)
{
    float x = mod(offset,32.);
    float y = offset / 32.;
    return vec2(x,y)/32.;
}

void main() {
    //st represents the position from 0. to 1. on the x and y axes where the pixel lives
    //this convention is adopted from thebookofshaders.com
    vec2 st = gl_FragCoord.xy/u_resolution;
    
    //the 3 at the beginning takes you to the midi continuous controllers
    //21, 22, and 23 are the addresses for the continuous controllers I am using for r, g, and b
    //I found these using components, the configuration software for my novation controller
    
    float ccr = 3. * 127. + 21.;
    float ccg = 3. * 127. + 22.;
    float ccb = 3. * 127. + 23.;
    
    //now we can use texture2D and midiCoord to pull r, g, and b values fro the 4th dimension of the sample
    float r = texture2D(u_midi,midiCoord(ccr)).w;
    float g = texture2D(u_midi,midiCoord(ccg)).w;
    float b = texture2D(u_midi,midiCoord(ccb)).w;
    

    gl_FragColor = vec4(r,g,b,1.);
}
```
