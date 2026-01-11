# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Hugo theme** for building digital gardens, inspired by Maggie Appleton's website. It is NOT a standalone project - there is no npm/build system. The theme extends Hugo with custom templates, styles, and layouts.

## Development Commands

This theme must be tested from a Hugo site, not standalone:

```bash
# Test from the exampleSite directory
cd exampleSite && hugo server --themesDir ../

# Build production site
hugo
```

## Architecture

### Three Content Sections

| Section | Content Type | Taxonomy |
|---------|-------------|----------|
| `/garden/` | Blog posts and articles | `garden_tags` |
| `/projects/` | Portfolio items | `project_tags` |
| `/library/` | Book notes | `library_tags` |

### Content Status System

All content uses a `status` frontmatter field that renders visual indicators:
- `seeding` - New posts ("Seeding")
- `growing` - In progress ("Growing")
- `evergreen` - Complete ("Evergreen")

### Template Hierarchy

1. **Base template**: `layouts/_default/baseof.html` - HTML skeleton with blocks for `head`, `header`, `main`, `footer`
2. **Home page**: `layouts/index.html` - Three-column layout showing Garden, Projects, Library
3. **Section templates**: `garden/list.html`, `projects/list.html`, `library/list.html` - Isotope-filtered grids
4. **Partials**: Reusable components in `layouts/partials/` (head, header, cards, status, scripts)
5. **Shortcodes**: Image processing, Mermaid diagrams, Bootstrap grid

### Key Partials
- `card_garden.html`, `card_project.html`, `card_book.html` - Content cards
- `status.html` - Renders seed/grow/evergreen status
- `script.html` - Loads jQuery, Isotope, Mermaid, dark mode toggle

### Client Libraries (static/)
- Bootstrap 5 - Grid and components
- FontAwesome 6 - Icons
- jQuery 3.x - DOM manipulation
- Isotope - Masonry layout and filtering
- Mermaid - Diagram rendering

## Configuration

Users configure the theme in their site's `config.toml`:

```toml
[params]
  name = "Your Name"
  description = "Your bio"
  initials = "NP"  # Shows in header instead of full name
  darkModeDefault = "light"  # Optional default theme

[taxonomies]
  garden_tags = 'garden_tags'
  project_tags = 'project_tags'
  library_tags = 'library_tags'
```

## Customization

Users can override styles by creating `./static/css/my_style.css` in their Hugo site - this file automatically overrides the theme's CSS.
