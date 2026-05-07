# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-file static landing page for the "Claude Code 101" PDF guide. Hosted on GitHub Pages at **https://stormlarsen.github.io/claude-code-101**.

## Architecture

The site consists of two files — no build step, no dependencies, no bundler:

- `index.html` — the landing page (~7 KB)
- `Claude-Code-101.pdf` — the guide, served as a separate file (~162 KB)

Download links use `<a href="Claude-Code-101.pdf" download="Claude Code 101.pdf">`. The PDF was previously embedded as a base64 data URI, but that approach was dropped because iOS Safari blocks data URI downloads.

On iPhone/iPad a JavaScript snippet detects iOS and shows a hint below the download button: *"PDF åbnes i Safari — tryk på Del-ikonet (□↑) og vælg 'Gem i Filer'"*. This is unavoidable — iOS Safari opens same-origin PDFs inline regardless of the `download` attribute.

## Deploying changes

```powershell
git add index.html
git commit -m "describe change"
git push
```

GitHub Pages deploys automatically from the `main` branch within ~1 minute.

## Updating the PDF

Replace `Claude-Code-101.pdf` with the new file (keep the same filename), then commit and push:

```powershell
git add Claude-Code-101.pdf
git commit -m "Update PDF"
git push
```

## Design tokens

All colours and key values are CSS custom properties at the top of the `<style>` block:

| Variable | Value | Use |
|---|---|---|
| `--orange` | `#f97316` | Primary accent, buttons, stats |
| `--bg` | `#fdf8f2` | Page background (warm cream) |
| `--text` | `#1c1410` | Body text |
| `--muted` | `#5c4f42` | Secondary text |

Font: **Inter** (Google Fonts), weights 600–900 throughout.
