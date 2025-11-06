# MickGeekLabs Portfolio Website

A modern, single-page portfolio and blog website built with Hugo static site generator and Tailwind CSS v4.

## 🚀 Features

- **Single-page design** with smooth anchor navigation
- **Dynamic content sections**: Hero, About, Projects, Blog, Contact
- **Hugo static site generator** for fast, efficient builds
- **Tailwind CSS v4** with custom theme configuration
- **Dark theme** with slate color palette
- **Responsive design** optimized for all devices
- **Blog system** with markdown support and syntax highlighting
- **Project showcase** with tech stack tags and GitHub links
- **Social media integration** (GitHub, Mastodon, Bluesky, Email)

## 📋 Prerequisites

- **Hugo Extended** v0.142.0 or higher ([Download](https://gohugo.io/installation/))
- **Git** for version control
- A modern web browser for testing

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd mgl-website
   ```

2. **Verify Hugo installation**
   ```bash
   hugo version
   ```
   Ensure you have the extended version installed.

## 💻 Development

### Start the Development Server

```bash
# Start server with drafts enabled (recommended for local development)
hugo server -D

# Start server without drafts
hugo server

# Start server on all network interfaces (for testing on other devices)
hugo server --bind 0.0.0.0
```

The site will be available at `http://localhost:1313/`

### Create New Content

```bash
# Create a new blog post
hugo new content/blog/my-new-post.md

# Create a new project page
hugo new content/projects/my-project.md
```

**Note**: New content is created with `draft = true` by default. Set `draft = false` or remove the line before publishing.

## 🏗️ Building for Production

```bash
# Build the static site
hugo

# Build with drafts included (not recommended for production)
hugo -D

# Clean build cache and output
rm -rf public/ .hugo_build.lock resources/
```

The built site will be in the `public/` directory, ready for deployment.

## 📁 Project Structure

```
.
├── archetypes/          # Content templates
├── assets/
│   └── css/
│       └── main.css     # Tailwind CSS v4 configuration
├── content/
│   ├── _index.md        # Homepage metadata
│   ├── blog/            # Blog posts
│   └── projects/        # Project pages
├── layouts/
│   ├── _default/
│   │   ├── baseof.html  # Base template
│   │   ├── single.html  # Post/project layout
│   │   └── list.html    # Archive pages
│   ├── partials/        # Reusable components
│   │   ├── css.html     # Tailwind processor
│   │   ├── header.html  # Navigation
│   │   └── footer.html  # Footer
│   └── index.html       # Homepage layout
├── static/              # Static assets (images, files)
├── hugo.toml            # Site configuration
└── README.md
```

## 🎨 Customization

### Site Configuration

Edit `hugo.toml` to customize:
- Site title and description
- Base URL
- Social media links
- Navigation menu items

### Styling

The site uses Tailwind CSS v4 with a custom theme:

- **Main stylesheet**: `assets/css/main.css`
- **Global styles**: `layouts/_default/baseof.html` (in `<style>` block)
- **Color palette**: Slate/Indigo/Emerald theme

**Color scheme:**
- Background: `#0f172a` (slate-900)
- Text: `#e2e8f0` (slate-200)
- Primary: `#4f46e5` (indigo-600)
- Accent: `#10b981` (emerald-500)

### Content Front Matter

**Blog posts** (`content/blog/`):
```yaml
title: "Post Title"
date: 2025-01-15
tags: ["tag1", "tag2"]
draft: false
```

**Projects** (`content/projects/`):
```yaml
title: "Project Name"
date: 2025-01-15
tech: ["Hugo", "Tailwind", "JavaScript"]
repo_url: "https://github.com/username/repo"
repo_text: "View Code on GitHub"  # Optional
```

## 📝 Content Guidelines

### Blog Posts
- Located in `content/blog/`
- Written in Markdown
- Support for code syntax highlighting
- Tags for categorization
- Most recent 3 posts appear on homepage

### Projects
- Located in `content/projects/`
- Include tech stack tags
- Link to GitHub repository
- Most recent 2 projects appear on homepage

## 🌐 Deployment

The site generates static HTML that can be deployed to any web hosting service:

- **GitHub Pages**: Deploy from `public/` directory
- **Netlify**: Connect repository and set build command to `hugo`
- **Vercel**: Auto-detects Hugo projects
- **Traditional hosting**: Upload contents of `public/` directory

## 🔧 Troubleshooting

**Hugo not found**: Ensure Hugo Extended is installed and in your PATH

**Styles not loading**: Check that `hugo_stats.json` is being generated (requires Hugo build)

**Drafts not showing**: Use the `-D` flag with `hugo server`

**Build errors**: Try cleaning the cache:
```bash
rm -rf public/ .hugo_build.lock resources/
hugo
```

## 📄 License

[Add your license information here]

## 👤 Author

**MickGeekLabs**
- Website: [mickgeeklabs.org](https://mickgeeklabs.org)
- GitHub: [@mickgeeklabs](https://github.com/mickgeeklabs)

## 🙏 Acknowledgments

- Built with [Hugo](https://gohugo.io/)
- Styled with [Tailwind CSS](https://tailwindcss.com/)
- Font: [Inter](https://fonts.google.com/specimen/Inter)
