<!--
Sync Impact Report:
Version change: Initial → 1.0.0
Added principles: Static-First, CDN-Ready, Minimal Dependencies, Performance-First, Simple Deployment
Added sections: Development Workflow
Templates requiring updates: ✅ All templates validated for consistency
Follow-up TODOs: None
-->

# No-Google-No-AI Constitution

## Core Principles

### I. Static-First
Static files only - no server-side processing, databases, or dynamic content generation. HTML, CSS, JavaScript, and assets must be servable directly from a CDN. All content must be pre-built and self-contained.

**Rationale**: Eliminates complexity, reduces attack surface, ensures maximum compatibility with CDN deployment.

### II. CDN-Ready
All paths must be relative or absolute, no localhost dependencies, and all assets must be optimized for CDN delivery (minified CSS/JS, compressed images, proper caching headers via meta tags).

**Rationale**: Ensures seamless deployment to Netlify, GitHub Pages, or any static hosting provider.

### III. Minimal Dependencies
Prefer vanilla HTML/CSS/JS over frameworks. When libraries are necessary, use CDN-hosted versions or single-file includes. No build tools unless absolutely required for basic optimization.

**Rationale**: Reduces bundle size, eliminates build complexity, improves maintainability.

### IV. Performance-First
Pages must load in under 2 seconds on 3G. Images optimized, CSS/JS minified, minimal HTTP requests. No unnecessary animations or heavy libraries.

**Rationale**: Ensures good user experience across all connection speeds and devices.

### V. Simple Deployment
Deployment must be a single step: push to repository or drag-and-drop to CDN. No build pipelines, environment variables, or configuration files required.

**Rationale**: Reduces deployment friction and maintenance overhead.

## Development Workflow

### File Organization
- `index.html` at root for homepage
- `css/` for stylesheets
- `js/` for JavaScript
- `images/` for media assets
- `pages/` for additional HTML pages

### Quality Gates
- All HTML must validate via W3C validator
- CSS must be browser-compatible (no experimental features)
- JavaScript must work without transpilation
- All links must be functional and relative
- Images must be optimized (<100KB each)

### Testing Requirements
- Manual testing in Chrome, Firefox, Safari
- Mobile responsiveness verification
- Load time testing on slow connections
- All forms and interactions must work with JavaScript disabled

## Governance

This constitution supersedes all other development practices. Any deviation from static-first principles must be explicitly justified and documented. Changes to this constitution require updating all dependent templates and documentation.

All code reviews must verify constitutional compliance. Complexity additions require clear justification showing simpler alternatives were insufficient.

**Version**: 1.0.0 | **Ratified**: 2025-09-25 | **Last Amended**: 2025-09-25