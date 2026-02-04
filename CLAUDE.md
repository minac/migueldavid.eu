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
- `work.json` - Work history for timeline (company, title, startDate, endDate)

### Layout Structure

The site uses a custom theme (`themes/hygge/`) with specialized layouts:

**Homepage (`themes/hygge/layouts/home.html`):**

- Header with butterfly logo, name, bio, social links
- Sections: Highlights, Projects, Writing, Talks
- Each section uses `.section-header` with title + "View More" link
- Content rendered as cards (`.card`) in grid layout (`.grid`)

**About page (`layouts/about.html`):**

- Custom layout outside theme
- Header with bio from `site.Params.aboutBio`
- Background section: first 3 items from `aboutsections.json` as cards
- Additional Info section: remaining items from `aboutsections.json`
- Work History section: vertical timeline from `work.json` with alternating left/right layout
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
- `params.bio` - Short tagline/bio (used on homepage)
- `params.aboutBio` - Longer bio text (used on about page)
- `params.blogURL` - External blog link
- `params.social.*` - Social media URLs (twitter, bluesky, github, linkedin)

## CSS Variables

Custom CSS variables in `themes/hygge/static/css/main.css`:

- `--color-bg` - Off-white background (#fffcf5)
- `--color-text` - Primary text color (#1a1a1a)
- `--color-text-light` - Secondary text (#666)
- `--color-text-lighter` - Tertiary text for dates (#999)
- `--color-border` - Subtle borders (#e5e3df)
