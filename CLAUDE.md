# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A plain static HTML/CSS/JS site with no build step, package manager, linter, or test suite. Node.js is not installed on the dev machine; do not introduce npm-based tooling without asking.

## Running locally

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000. The `web` entry in `.claude/launch.json` runs the same server via `/bin/sh`, using the absolute Python path (`python3` is not on the desktop app's PATH) and `$PORT` with `autoPort` so it picks another port if 8000 is taken (the user sometimes runs their own server on 8000).

## Deployment

The repo is `petgeb/NewTest1` (public). GitHub Pages serves the root of `main` at https://petgeb.github.io/NewTest1/, so every push to `main` deploys. Because the site lives under the `/NewTest1/` subpath, keep asset references relative (`css/styles.css`, not `/css/styles.css`).

## Structure

- `index.html` loads `css/styles.css` and `js/main.js` (as an ES module).
- Theme colors are CSS custom properties on `:root` in `css/styles.css`, with dark-mode overrides in a `prefers-color-scheme: dark` block. A color change (e.g. the button's `--accent`) must be made in both places.
