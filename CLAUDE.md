# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A static site published with GitHub Pages. There is no build step, package manager, linter or test suite — files are served exactly as committed. Currently the site is a single placeholder `index.html`.

## Running locally

Serve the repo root with any static file server, e.g.:

```
python3 -m http.server 8000
```

## Deployment

`.github/workflows/pages.yml` deploys on every push to `main` (or manual `workflow_dispatch`). It uploads the **entire repository root** (`path: .`) as the Pages artifact, so every committed file becomes publicly reachable on the site — not just HTML. If you add files that shouldn't be served, either keep them out of the repo or change the workflow to publish a dedicated subdirectory.

## Public repo / secrets

The repo is public. `.gitignore` excludes `.env*` (except `.env.example`), key/cert files (`*.pem`, `*.key`, `*.p12`, `*.pfx`, `id_rsa*`, `id_ed25519*`), anything matching `*credentials*` or `*secret*`, and `*.sqlite` / `*.db`. Note the `*secret*` / `*credentials*` globs will also silently ignore legitimate source files with those words in their names.
