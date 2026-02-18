# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A minimal personal website built with Hugo, embracing hygge editorial minimalism. Single-page layout with clean typography (Playfair Display headings, Sora body), generous whitespace, and warm, calm aesthetics (off-white backgrounds, soft contrast).

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
- `writing.json` - Blog posts with optional URLs (points to blog.migueldavid.eu)
- `talks.json` - Speaking engagements with language tags
- `opensource.json` - OSS contributions with status labels
- `aboutsections.json` - Background sections with title/description/items
- `work.json` - Work history for timeline (company, url, title, startDate, endDate, description)
- `consulting.json` - Consulting services and project history

### Layout Structure

The site uses a custom theme (`themes/hygge/`) with specialized layouts:

**Homepage (`themes/hygge/layouts/home.html`):**

- Hero: big name (Playfair Display), tagline, two-column layout
- Left column: About bio, Work History timeline (from `work.json`)
- Right column: sticky photo
- Background cards from `aboutsections.json`
- Sections (alphabetical): Blog, Consulting, Projects, Talks
- Each section uses `.section-header` with title + link
- Content rendered as cards (`.card`) in grid layout (`.grid`)

**Consulting page (`layouts/consulting.html`):**

- Services section with cards
- Selected Projects section using shared `.about-timeline` styles

**Projects page (`layouts/projects.html`):**

- Displays all projects from `data/projects.json`

**Shared navigation (`themes/hygge/layouts/_partials/nav.html`):**

- Included on all pages via `baseof.html`
- Butterfly logo, site name, nav links (Blog, Consulting, Projects), social icons

### Styling Pattern

Cards use consistent classes:

- `.card` - Container
- `.card-title` - Heading (Playfair Display serif)
- `.card-description` - Body text
- `.card-links` - Icon links (GitHub, website, npm, etc.)

Timeline uses shared classes (in `main.css`):

- `.about-timeline` - Container with vertical line
- `.about-timeline-entry` - Entry with dot marker
- `.about-timeline-role` - Job title (Playfair Display serif)
- `.about-timeline-date` - Date range
- `.about-timeline-company` - Company name with optional link
- `.about-timeline-desc` - Description text

Social/external links use inline SVG icons with consistent styling.

## Design Philosophy

- Typography-first: Playfair Display for headings, Sora for body
- No cluttered SaaS/marketing vibes
- Scroll-driven single-page homepage
- All styling in `themes/hygge/static/css/main.css` (avoid `themes/hygge/assets/css/`)

## Configuration

Site config in `hugo.toml`:

- `params.name` - Site/personal name
- `params.bio` - Short tagline/bio (used on homepage hero)
- `params.aboutBio` - Longer bio text (used in about section)
- `params.blogURL` - External blog link (blog.migueldavid.eu)
- `params.social.*` - Social media URLs (twitter, bluesky, github, linkedin)

## CSS Variables

Custom CSS variables in `themes/hygge/static/css/main.css`:

- `--color-bg` - Off-white background (#fffcf5)
- `--color-text` - Primary text color (#1a1a1a)
- `--color-text-light` - Secondary text (#666)
- `--color-text-lighter` - Tertiary text for dates (#999)
- `--color-border` - Subtle borders (#e5e3df)
- `--font-serif` - Playfair Display stack
- `--font-sans` - Sora stack
- `--max-width` - Container width (960px)

## Gotchas

- CSS lives in `themes/hygge/static/css/main.css`, NOT `themes/hygge/assets/css/main.css` (the assets version is a minimal fallback)
- Google Fonts loaded via `<link>` in `baseof.html`, not Hugo Pipes
- Hugo's `with` changes context — use `$variable := .field` before `with` blocks to preserve outer scope values
- `/about` redirects to `/` via Hugo alias in `content/_index.md`
- Browser may cache old CSS aggressively — use `hugo server --noHTTPCache` and hard-refresh when debugging styles
