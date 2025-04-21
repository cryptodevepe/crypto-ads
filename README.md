# Crypto Ads Platform

A Hugo-based website for cryptocurrency advertising monetization using the Stack theme.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Content Management](#content-management)
- [Ad Integration](#ad-integration)
- [Deployment](#deployment)
- [Development](#development)
- [GitHub Updates](#github-updates)
- [Troubleshooting](#troubleshooting)

## Overview
This project provides a platform for content creators to monetize their websites through cryptocurrency advertising networks. Built with Hugo and the Stack theme, it offers a fast, SEO-friendly solution with built-in ad placements.

## Features
- **Ad Integration**:
  - A-Ads sidebar (300x250)
  - Bitmedia header (728x90)
  - Flexible ad zone placement
- **Content Management**:
  - Markdown-based content
  - Category and tag support
  - SEO optimized
- **Design**:
  - Responsive layout
  - Dark/light mode
  - Mobile-first approach
- **Performance**:
  - Fast loading times
  - Optimized asset delivery
  - Minimal JavaScript

## Prerequisites
- Hugo (v0.111.0 or later)
- Git
- Node.js (for development)
- Basic command line knowledge

## Installation
```bash
# Create new site
hugo new site crypto-ads
cd crypto-ads

# Add theme
git init
git submodule add https://github.com/CaiJimmy/hugo-theme-stack themes/stack

# Copy configuration (using hugo.yaml)
cp themes/stack/exampleSite/config.yaml hugo.yaml
```

## Configuration
```yaml
# Basic site configuration (matches /crypto-ads/hugo.yaml)
baseURL: 'https://cryptodev.top'
title: 'Crypto Earnings'
theme: stack
enableRobotsTXT: true

# Theme parameters
params:
  mainSections: ['posts']
  sidebar:
    subtitle: 'Learn crypto ad monetization'
  widgets:
    left:
      - type: custom
        name: "a-ads-sidebar"
```

## Content Management
```bash
# Create essential pages
hugo new _index.md      # Homepage
hugo new about.md       # About page
hugo new posts/first.md # Blog post

# Content structure
content/
├── _index.md          # Homepage
├── about.md           # About page
└── posts/             # Blog posts
    └── *.md
```

## Ad Integration
1. **A-Ads Setup**:
```html
<!-- layouts/partials/widgets/a-ads-sidebar.html -->
<script async src="https://a-ads.com/[YOUR-CODE].js"></script>
```

2. **Bitmedia Setup**:
```html
<!-- layouts/partials/header/ads.html -->
<script src="https://bitmedia.io/[YOUR-CODE].js"></script>
```

## Deployment
1. **Netlify Configuration**:
```toml
[build]
  publish = "public"
  command = "hugo"

[build.environment]
  HUGO_VERSION = "0.111.0"
```

2. **Deploy Command**:
```bash
# Build site
hugo --minify

# Test build
hugo server --disableFastRender
```

## Development
```bash
# Start development server
hugo server -D --bind=0.0.0.0

# Access local site
http://localhost:1313
```

## GitHub Updates

### Basic Update Flow
```bash
# Check status of changes
git status

# Stage all changes
git add .

# Commit changes with message
git commit -m "Update site content"

# Push to main branch
git push origin main
```

### Common Git Tasks
```bash
# Update from remote
git pull origin main

# View commit history
git log --oneline

# Discard local changes
git checkout -- .
```

### Troubleshooting Git
- **Authentication Failed**: Re-configure credentials:
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "your@email.com"
  ```
- **Merge Conflicts**: Resolve and continue:
  ```bash
  git status                 # Check conflict files
  git add <resolved-files>   # Stage resolved files
  git commit -m "Fix merge conflicts"
  ```

## Troubleshooting

### Site Not Found on Netlify
- Verify that your repository is connected in the Netlify dashboard.
- Confirm your build settings:
  - Build command: `hugo --gc --minify`
  - Publish directory: `public`
  - Hugo version is set (see `netlify.toml` example below):
    ```toml
    [context.production.environment]
      HUGO_VERSION = "0.125.7"
    ```
- Test the site locally with:
  ```bash
  hugo server -D
  ```
- For custom domains, ensure proper DNS records (A/CNAME) point to Netlify.
- Trigger a redeploy and clear the build cache if issues persist.

### Common Issues
1. **Ads Not Displaying**
- Verify ad network approval
- Check ad blocker settings
- Validate ad zone IDs

2. **Build Errors**
```bash
# Clear cache and rebuild
rm -rf public/
hugo server --disableFastRender
```

### Best Practices
- Keep ad placements user-friendly
- Monitor ad performance regularly
- Update content frequently
- Maintain SEO optimization
- Use semantic versioning

## License
MIT License - See [LICENSE](LICENSE) for details.