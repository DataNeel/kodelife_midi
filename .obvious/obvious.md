# Obvious repo guidance

<!-- obvious-install: skill=autobuild-setup, skill-version=1.0.3, template-version=1 -->

This repo uses `.obvious/` for reviewed Autobuild guidance.

Before editing, suggest the smallest relevant set of `.obvious` files for the task. Match candidate files by reading their frontmatter.

## Codebase Map

This is a single-file repo. The entire codebase is a GLSL fragment shader embedded in `README.md`.

| Path | Purpose |
|---|---|
| `README.md` | GLSL shader source + documentation for KodeLife MIDI integration |

No subdirectories, no build system, no package manager, no CI.

## Repo Guidance for Autobuild

<!-- synthesized from: README.md — the only documentation file in the repo -->

- **Language:** GLSL (OpenGL Shading Language) — fragment shader for KodeLife
- **Purpose:** Demonstrates MIDI continuous controller → RGB color mapping via KodeLife's built-in MIDI sampler uniform
- **No build system:** The shader is loaded directly into KodeLife (a live shader editor by Hexler). There is no compilation step, package manager, or test runner.
- **No test commands:** No tests exist. Verification is visual (shader output in KodeLife).
- **No lint commands:** No linter configured.
- **Commit convention:** Historical commits use short imperative summaries ("Update README.md", "first commit").

## Local Verification

> **Scaffold branch:** This repo has no runnable stack — no package.json, no build system, no server, no test runner. Local dev verification was skipped per the autobuild-setup SCAFFOLD branch.

### Verified Commands

Not applicable — no build, lint, or test commands exist in this repo.

### Scoped Workflow

Not applicable — no toolchain to scope.

## Sandbox Snapshot

- **Snapshot ID:** N/A
- **Captured:** 2026-08-11T00:00:00Z
- **Dev stack healthy:** no — no runnable stack in this repo

> **Note:** Snapshot skipped — dev stack not healthy. Repo contains only a README.md with embedded GLSL shader code; no build system or runtime to snapshot.

## Bibliography

- **Nodes upserted:** 1 (created)
- **Slugs:** `kodelife-midi-shader`
- **Node ID:** `bib_E6vp241u`
- **Type:** concept
- **Description:** GLSL fragment shader that reads MIDI continuous controller values via KodeLife's built-in MIDI sampler uniform, mapping CC values to RGB color channels for generative art.
- **Source:** `README.md` (file-level provenance)

## Security Scan

> **Note:** security_scan_not_triggered — no trigger_security_onboarding tool available in this worker's toolset. Trigger manually if needed.

## Runbooks

Populated by autobuild-runbooks skill when requested. See `.obvious/runbooks/` after that skill runs.
