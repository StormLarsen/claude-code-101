# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-file static landing page for the "Claude Code 101" PDF guide. Hosted on GitHub Pages at **https://stormlarsen.github.io/claude-code-101**.

## Architecture

The entire site is `index.html` — no build step, no dependencies, no bundler. The PDF is embedded directly as a base64 data URI inside the download `<a>` tags, making the file self-contained (~440 KB). Anyone who opens the HTML file can download the PDF without needing the original PDF file present.

## Deploying changes

```powershell
git add index.html
git commit -m "describe change"
git push
```

GitHub Pages deploys automatically from the `main` branch within ~1 minute.

## Updating the embedded PDF

If the PDF changes, re-encode it and inject it into the `href` attributes of all download links:

```powershell
$b64 = [Convert]::ToBase64String([IO.File]::ReadAllBytes("path\to\new.pdf"))
# Replace the data URI in index.html manually or via script
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
