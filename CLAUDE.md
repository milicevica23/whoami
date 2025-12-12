# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a personal blog website built with Hugo using the Hugo Blox Builder framework (formerly Hugo Academic/Wowchemy). The site uses Tailwind CSS v4 for styling and is deployed on Netlify.

**Live Site:** https://milicevica.com

## Development Commands

### Local Development
```bash
npm run dev
# or with pnpm
pnpm dev
```
This runs `hugo server --disableFastRender` which starts the development server with hot reloading.

### Build
```bash
npm run build
# or with pnpm
pnpm build
```
This runs `hugo --minify` to generate the production build in the `public/` directory.

### Install Dependencies
```bash
pnpm install
```
**Note:** This project uses pnpm v10.14.0 as the package manager (specified in package.json).

## Architecture

### Framework: Hugo Blox Builder
This site uses Hugo Blox (v2.0 schema), a modular Hugo theme system. The architecture is module-based:

**Hugo Modules (go.mod):**
- `blox-plugin-netlify`: Netlify-specific features and optimizations
- `blox-tailwind`: Tailwind CSS v4 integration

**Custom Blox Components:** Located in `hugo-blox/blox/`:
- `community/`: Community-contributed blocks
- `all-access/`: Premium/custom blocks

These are mounted into Hugo's layout system via `module.yaml` configuration.

### Configuration System

Hugo Blox uses a layered configuration approach:

**Primary Config Files (config/_default/):**
- `hugo.yaml`: Core Hugo settings, build options, cascade rules for content types
- `params.yaml`: Hugo Blox configuration (theme, layout, analytics, SEO, features)
- `module.yaml`: Hugo modules and mount points for custom blox
- `menus.yaml`: Site navigation structure
- `languages.yaml`: Internationalization settings

**Build Config:**
- `netlify.toml`: Netlify build commands, environment variables, deploy contexts
- `hugoblox.yaml`: Template metadata and Hugo version requirement

### Content Organization

Content follows Hugo's content structure:

**Main Content Directories:**
- `content/blog/`: Blog posts (each post is a folder with `index.md` and assets)
- `content/events/`: Event posts
- `content/authors/`: Author profile pages (_index.md only, actual author data in `data/authors/`)
- `content/tags/`: Tag taxonomy pages
- `content/_index.md`: Homepage (uses Hugo Blox landing page type with sections/blocks)

**Author System:**
Author profiles are defined in `data/authors/<slug>.yaml` and referenced throughout the site. Avatar images go in `assets/media/authors/<slug>.jpg`.

**Page Types:**
- Blog posts: Regular content with frontmatter (title, date, summary, etc.)
- Landing pages: Use `type: landing` with block-based sections in frontmatter
- Events: Similar to blog posts but in events/ folder

### Styling

**Tailwind CSS v4:** The project uses the latest Tailwind CSS (v4.1.12) via `@tailwindcss/cli`.

**Theme Customization:** Configured in `params.yaml` under `hugoblox.theme`:
- Color schemes (light/dark/system mode)
- Typography (font family, size)
- Layout (spacing, radius, avatar shapes)

### Build Process

**Development:** Hugo's built-in server with fast refresh.

**Production (Netlify):**
1. Install pnpm dependencies
2. Run `hugo --gc --minify` with environment-specific flags
3. Run `pagefind` for search indexing
4. Publish from `public/` directory

**Environment Variables (Netlify):**
- `HUGO_VERSION`: 0.152.2
- `GO_VERSION`: 1.21.5
- `NODE_VERSION`: 22
- `HUGO_ENV`: production (in production context)

### Key Features

**Enabled Features (params.yaml):**
- Google Analytics (G-NCF6LWRES5)
- Site search (Pagefind-based)
- Theme toggle (light/dark mode)
- Reading time estimates
- Table of contents
- Related content suggestions
- Social sharing
- Sticky navbar

**Content Features:**
- Blog posts support reading time, comments (disabled), sharing, related posts
- Math rendering (disabled by default)
- Markdown, LaTeX, diagrams support
- Citation styles (APA/MLA/Chicago/IEEE)

## Important Notes

**Hugo Version:** This site requires Hugo v0.152.2 (extended version for Tailwind support).

**Package Manager:** Use pnpm, not npm or yarn. The lockfile is package-lock.json but packageManager is set to pnpm@10.14.0.

**Content Creation:** When adding blog posts, create a folder in `content/blog/<post-slug>/` with an `index.md` file. Images and assets go in the same folder.

**Author Updates:** Edit `data/authors/me.yaml` to update author information. Avatar images go in `assets/media/authors/`.

**Custom Blocks:** Custom Hugo Blox components in `hugo-blox/blox/` are mounted via `module.yaml` and can be used in landing pages.

**Deployment:** The site auto-deploys to Netlify on git push. Deploy previews are created for PRs.
