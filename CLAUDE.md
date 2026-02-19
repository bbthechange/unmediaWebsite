# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static website for **Unmedia Social LLC** (unmediasocial.com). Serves a landing page and versioned legal documents (privacy policies, terms & conditions) for multiple apps. Currently hosts documents for **Slanga**. No build system, no dependencies — just plain HTML/CSS files served statically.

## Repository Structure

- `index.html` — Landing page
- `legal/{app-name}/{doc-type}/` — Legal documents per app
- `context/legal-documents.md` — **Read this before modifying legal documents.** Contains the directory conventions, HTML template, and versioning rules.
- `images/` — Site images
- `favicon.ico`, `favicon.png` — Favicons

## Legal Documents System

Documents follow a strict versioning scheme described in `context/legal-documents.md`. Key rules:

- Path pattern: `legal/{app-name}/privacy-policy/` and `legal/{app-name}/terms-and-conditions/`
- Versions are `v1.html`, `v2.html`, etc. `latest.html` is always an exact copy of the highest version.
- App names are lowercase, hyphenated (e.g., `slanga`)
- **Never modify the legal text body** — only wrap it in the HTML template from `context/legal-documents.md`
- If source HTML has Cloudflare email obfuscation, decode it back to plain `mailto:` links

## Deployment

Served via Cloudflare at https://unmediasocial.com/. Source repo: `bbthechange/unmediaWebsite`.
