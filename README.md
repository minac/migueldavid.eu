# migueldavid.eu

A minimal, calm personal website built with Hugo. Embraces hygge editorial minimalism with clean typography, generous whitespace, and a focus on content.

## Design Philosophy

- **Warm & calm**: Off-white backgrounds with soft contrast
- **Typography-first**: Content hierarchy through type, not boxes
- **Minimal navigation**: Single-page scroll-driven layout
- **Generous whitespace**: Breathing room for content
- **No clutter**: Zero SaaS/marketing vibes

## Development

### Prerequisites

- [Hugo](https://gohugo.io/) v0.155.2 or later

### Running locally

```bash
hugo server
```

Visit http://localhost:1313

### Building for production

```bash
hugo
```

Static files will be generated in the `public/` directory.

## Project Structure

```
.
├── data/               # Content data files
│   ├── projects.json   # Project listings
│   ├── writing.json    # Writing pieces
│   └── opensource.json # Open source contributions
├── themes/hygge/       # Custom theme
│   ├── layouts/        # HTML templates
│   └── static/css/     # Stylesheets
└── hugo.toml           # Site configuration
```

## Customization

### Site info

Edit `hugo.toml`:

```toml
[params]
  name = "Your Name"
  bio = "Your bio here"
  blogURL = "https://your-blog-url.com"

  [params.social]
    twitter = "https://x.com/yourhandle"
    github = "https://github.com/yourusername"
    linkedin = "https://linkedin.com/in/yourprofile"
```

### Projects

Edit `data/projects.json`:

```json
[
  {
    "title": "Project Name",
    "description": "Brief description",
    "github": "https://github.com/...",
    "website": "https://...",
    "npm": "https://npmjs.com/package/..."
  }
]
```

### Writing

Edit `data/writing.json`:

```json
[
  {
    "title": "Article Title",
    "description": "Brief description",
    "url": "/writing/article-slug"
  }
]
```

### Open Source Contributions

Edit `data/opensource.json`:

```json
[
  {
    "title": "Project Name",
    "statusLabel": "PR",
    "state": "OPEN",
    "date": "FEB 2025",
    "description": "What you contributed",
    "github": "https://github.com/..."
  }
]
```

## Deployment

This is a static site that can be deployed to any static hosting:

- **GitHub Pages**: Push `public/` directory
- **Netlify**: Connect your repo, build command: `hugo`, publish directory: `public`
- **Vercel**: Same as Netlify
- **Cloudflare Pages**: Same as Netlify

## License

Theme and content structure available under MIT License.
