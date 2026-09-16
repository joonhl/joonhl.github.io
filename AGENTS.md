# Project agent memory

This file is the project's committed home for project-intrinsic agent knowledge: build, test, release, architecture, and sharp-edge notes that should travel with the code.

## Project shape

This is a static GitHub Pages site served straight from the repository root: no build step, no bundler, no package manager, no backend, and no CI.
Every page is one self-contained `.html` file with its CSS and JS inline; keep it that way so a page can be opened directly from disk.
Third-party code is limited to CDN `<link>`/`<script>` tags, and any such dependency must degrade gracefully when it fails to load.

## Verifying a change

There are no automated checks, so verify visually in a real browser at both a desktop and a mobile viewport width.
Serve the directory first (`python3 -m http.server`) rather than opening `file://`, so relative links between pages behave as they do in production.

## Sharp edges

`palms-and-pointers.html` renders its background with a hand-written WebGL fragment shader.
GLSL `smoothstep(edge0, edge1, x)` is undefined when `edge0 >= edge1`; write `1.0 - smoothstep(lo, hi, x)` instead of swapping the edges.
The page must stay usable when WebGL is unavailable, so the CSS-gradient fallback path is part of the contract, not a nicety.

## Maintaining this file

Keep this file for knowledge useful to almost every future agent session in this project.
Do not repeat what the codebase already shows; point to the authoritative file or command instead.
Prefer rewriting or pruning existing entries over appending new ones.
When updating this file, preserve this bar for all agents and keep entries concise.
