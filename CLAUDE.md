# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A minimal personal website built with Hugo, embracing hygge editorial minimalism. Single-page layout with clean typography, generous whitespace, and warm, calm aesthetics (off-white backgrounds, soft contrast).

## Commands

**Development:**

```bash
hugo server         # Run dev server at http://localhost:1313
hugo server -D      # Include draft content
```

**Production:**

```bash
hugo                # Build static site to public/
```

## Architecture

### Content Model

Content is data-driven through JSON files in `data/`:

- `highlights.json` - Homepage highlights (3 cards)
- `projects.json` - Project listings with optional github/website/npm links
- `writing.json` - Writing pieces with optional URLs
- `talks.json` - Speaking engagements with language tags
- `opensource.json` - OSS contributions with status labels
- `aboutsections.json` - About page sections with title/description/items

### Layout Structure

The site uses a custom theme (`themes/hygge/`) with specialized layouts:

**Homepage (`themes/hygge/layouts/home.html`):**

- Header with butterfly logo, name, bio, social links
- Sections: Highlights, Projects, Writing, Talks
- Each section uses `.section-header` with title + "View More" link
- Content rendered as cards (`.card`) in grid layout (`.grid`)

**About page (`layouts/about.html`):**

- Custom layout outside theme
- Two sections: first 3 items from `aboutsections.json` as cards, remaining items below
- Items with `items` array render as checkmarked bullet points (✓)
- Items with `description` render as paragraph text

**Projects page (`layouts/projects.html`):**

- Displays all projects from `data/projects.json`

### Styling Pattern

Cards use consistent classes:

- `.card` - Container
- `.card-title` - Heading
- `.card-description` - Body text
- `.card-links` - Icon links (GitHub, website, npm, etc.)

Social/external links use inline SVG icons with consistent styling.

## Design Philosophy

- Typography-first: Content hierarchy through type, not boxes
- No cluttered SaaS/marketing vibes
- Minimal navigation: scroll-driven single-page
- All styling inline or in `themes/hygge/static/css/main.css`

## Configuration

Site config in `hugo.toml`:

- `params.name` - Site/personal name
- `params.bio` - Tagline/bio
- `params.blogURL` - External blog link
- `params.social.*` - Social media URLs (twitter, bluesky, github, linkedin)
