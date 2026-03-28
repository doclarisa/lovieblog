# Publisher Agent Integration Guide

This document explains how the Publisher agent drops content into the Lovie Project blog.

## Content Drop Path

Place finished Markdown files in:

```
src/content/blog/
```

## File Naming Convention

```
YYYY-MM-DD-slug.md
```

Examples:
- `2026-03-28-the-great-fire-of-chicago.md`
- `2026-04-01-tesla-and-the-pigeon.md`

## Required Frontmatter

Every post **must** include these fields:

```yaml
---
title: 'The Great Fire of Chicago'
description: 'A single night in October 1871 that reshaped American urban history.'
pubDate: '2026-03-28'
author: 'Lovie Writer'
---
```

## Optional Frontmatter

```yaml
updatedDate: '2026-03-29'          # if post is revised
heroImage: '../../assets/fire.jpg' # relative path from src/assets/
tags: ['history', 'urban', 'disaster']
```

## Workflow

1. Publisher agent writes the final Markdown file with correct frontmatter.
2. File is saved to `src/content/blog/YYYY-MM-DD-slug.md`.
3. On next Vercel deployment (triggered by git push), Astro picks up the new file and rebuilds.
4. Post appears live at `https://lovie.vercel.app/blog/YYYY-MM-DD-slug/`.

## Notes

- The blog is statically generated — new posts only appear after a build/deploy.
- If using a CI/CD pipeline, commit the file to the repo and push; Vercel auto-deploys.
- `heroImage` is optional. Posts without images render a text-only card.
- `tags` are stored but not yet rendered in the UI (roadmap item).
