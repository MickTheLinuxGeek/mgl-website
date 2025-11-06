# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a personal portfolio and blog website for MickGeekLabs, built with Hugo static site generator. The site is a single-page application with sections for about, projects, blog posts, tech stack, and contact information. The frontend uses Tailwind CSS v4 for styling with a dark theme (slate-900 background).

**Key characteristics:**
- Custom Hugo theme built from scratch (no theme dependency)
- Tailwind CSS v4 with Hugo integration (assets/css/main.css)
- Single-page homepage with anchor navigation
- Dynamic content sections for projects and blog posts
- Social media integration (GitHub, Mastodon, Bluesky, Email)

## Development Commands

### Local Development
```bash
# Start the Hugo development server with drafts enabled
hugo server -D

# Start server without drafts
hugo server

# Start server and bind to all interfaces (for testing on other devices)
hugo server --bind 0.0.0.0
```

### Building
```bash
# Build the site for production (output to 'public/' directory)
hugo

# Build with drafts included
hugo -D

# Clean build cache
rm -rf public/ .hugo_build.lock resources/
```

### Content Creation
```bash
# Create a new blog post (automatically uses archetype)
hugo new content/blog/post-name.md

# Create a new project page
hugo new content/projects/project-name.md

# Note: New content is created with 'draft = true' by default
# Remove this line or set to 'false' before building for production
```

## Architecture & Structure

### Directory Layout
```
.
├── archetypes/       # Content templates (default.md defines front matter)
├── assets/           # Asset processing
│   └── css/
│       └── main.css  # Tailwind CSS v4 entry point with @theme configuration
├── content/          # All markdown content
│   ├── _index.md     # Homepage metadata
│   ├── blog/         # Blog posts
│   └── projects/     # Project showcase pages
├── layouts/          # HTML templates
│   ├── _default/     # Default templates
│   │   ├── baseof.html   # Base template with <head>, includes css partial, global styles
│   │   ├── single.html   # Individual blog/project post layout
│   │   └── list.html     # List pages for blog archives, tags, etc.
│   ├── partials/     # Reusable components
│   │   ├── css.html      # Tailwind CSS processing partial
│   │   ├── header.html   # Sticky navigation header
│   │   └── footer.html   # Site footer
│   └── index.html    # Homepage single-page layout
├── static/           # Static assets (images, files)
├── data/             # Data files for Hugo (currently unused)
├── i18n/             # Internationalization (currently unused)
├── hugo.toml         # Site configuration
└── hugo_stats.json   # Generated file for Tailwind CSS class detection
```

### Template Hierarchy
1. **baseof.html** - Base template loaded for all pages
   - Loads Tailwind CSS via the css.html partial (processes assets/css/main.css)
   - Loads Inter font from Google Fonts
   - Defines global styles and CSS custom properties
   - Includes header and footer partials

2. **index.html** - Homepage layout (overrides main block)
   - Single-page sections: Hero, Focus, Projects, Blog, Contact
   - Dynamically loads recent projects from `content/projects/`
   - Dynamically loads recent blog posts from `content/blog/`
   - Uses Hugo's `.Site.Params.social` for contact links

3. **single.html** - Individual content pages
   - Blog post layout with prose styling
   - Displays title, date, tags
   - Renders markdown content with custom typography

4. **list.html** - Archive/taxonomy pages
   - Used for /blog/, /tags/, category pages
   - Lists posts with pagination support

### Content Structure

**Project Pages** (content/projects/)
- Front matter fields:
  ```yaml
  title: "Project Name"
  date: YYYY-MM-DD
  tech: ["Tech1", "Tech2"]  # Tech stack tags
  repo_url: "https://github.com/..."
  repo_text: "View Code on GitHub"  # Optional custom link text
  ```
- Only the 2 most recent projects appear on the homepage
- Projects are sorted by date (newest first)

**Blog Posts** (content/blog/)
- Standard Hugo front matter (title, date, tags, draft)
- Up to 3 most recent posts shown on homepage
- Full archive accessible at /blog/

### Styling System

**Tailwind CSS v4 Configuration:**
- Located in `assets/css/main.css`
- Uses `@theme` directive to define custom design tokens
- Sources class names from `hugo_stats.json` for purging
- Custom theme variables:
  - `--font-family-sans`: Inter font
  - `--color-primary`: #4f46e5 (indigo-600)
  - `--color-accent`: #10b981 (emerald-500)

**Color Palette:**
- Background: `#0f172a` (slate-900)
- Text: `#e2e8f0` (slate-200)
- Primary: `#4f46e5` (indigo-600) - links, accents
- Accent: `#10b981` (emerald-500) - secondary highlights
- Cards: `#1e293b` (slate-800)

**Custom CSS Classes:**
- `.container-padding` - Responsive padding (1rem on mobile, 2.5rem on desktop)
- `.section-separator` - Emerald horizontal divider bar
- `.line-clamp-3` - Truncate text to 3 lines with ellipsis
- `.prose` - Markdown content styling (headings, links, code blocks)

### Configuration (hugo.toml)

Key config sections:
- `baseURL` - Site URL (mickgeeklabs.org)
- `[params]` - Site description, custom parameters
- `[params.social]` - Social media links (GitHub, Mastodon, Bluesky, Email)
- `[menu.main]` - Navigation menu items with weights for ordering
- `[build]` - Build configuration for Tailwind CSS v4 integration
  - `[build.buildStats]` - Enables hugo_stats.json generation
  - `[[build.cachebusters]]` - Cache invalidation for CSS assets
- `[module]` - Module mounts for assets and hugo_stats.json

## Development Workflow

1. **Adding new content**: Use `hugo new` with the appropriate path. The archetype will populate front matter.

2. **Testing locally**: Always run `hugo server -D` to preview content including drafts.

3. **Styling changes**: 
   - Global styles go in `layouts/_default/baseof.html` `<style>` block
   - Tailwind classes can be used inline in templates
   - Tailwind theme config is in `assets/css/main.css` using `@theme` directive
   - Custom CSS can be added below the `@theme` block in main.css

4. **Layout modifications**:
   - Homepage sections: Edit `layouts/index.html`
   - Blog/project detail pages: Edit `layouts/_default/single.html`
   - Navigation: Edit `layouts/partials/header.html`

5. **Content organization**:
   - Blog posts go in `content/blog/`
   - Projects go in `content/projects/`
   - Use descriptive filenames (they become URL slugs)

## Hugo Version
This project uses Hugo v0.142.0+extended. The extended version is required for advanced features.
