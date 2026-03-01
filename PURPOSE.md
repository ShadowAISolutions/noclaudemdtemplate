# Repository Purpose

## Overview

**noclaudemdtemplate** is a starter template repository built by ShadowAISolutions. It provides an automated CI/CD pipeline for projects that use Claude-driven development branches (`claude/*`) with automatic merging and conditional deployment.

## What It Does

### Automated Branch Management
- Code pushed to any `claude/*` branch is **automatically merged into `main`** via GitHub Actions.
- Fast-forward merge is preferred; falls back to a merge with "theirs" strategy if needed.
- The `claude/*` branch is **deleted after a successful merge**.

### Conditional Deployments

The single GitHub Actions workflow (`auto-merge-claude.yml`) supports two deployment targets:

1. **GitHub Pages** — Static files in the `live-site-pages/` directory are deployed to GitHub Pages whenever they change.
2. **Google Apps Script (GAS)** — GAS projects stored in `googleAppsScripts/` (one folder per project, each with a `Code.gs` file) are deployed by calling the GAS web app endpoint when their script file changes.

Each deployment only runs when its relevant files are modified.

### Template Guard

The workflow checks for an `IS_TEMPLATE_REPO` flag in a `CLAUDE.md` file. If the flag matches the repo name, deployments are skipped. This repo intentionally **omits `CLAUDE.md`** (hence the name "noclaudemdtemplate"), ensuring deployments always proceed for repos created from this template.

## Repository Structure

```
.
├── .github/
│   └── workflows/
│       └── auto-merge-claude.yml   # Single CI/CD workflow
├── live-site-pages/
│   └── index.html                  # Static site content (deployed to GitHub Pages)
└── PURPOSE.md                      # This file
```

## How to Use

1. Create a new repository from this template.
2. Add static site content to `live-site-pages/`.
3. Optionally add Google Apps Script projects under `googleAppsScripts/` (see the workflow file for detailed setup instructions).
4. Push changes to a `claude/*` branch — the workflow handles merging and deploying automatically.
