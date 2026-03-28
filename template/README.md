# PRD Template

A reusable PRD (Product Requirements Document) template with built-in Light/Dark theme, CN/EN language toggle, Mermaid diagrams, and responsive sidebar navigation.

## Quick Start

1. Copy `prd_template.html` to your project folder:
   ```bash
   cp template/prd_template.html <project-name>/prd_v1.0.html
   ```

2. Search and replace these placeholders:

   | Placeholder | Replace With |
   |---|---|
   | `{{PROJECT_NAME}}` | Your project name (e.g., "Linora") |
   | `{{PROJECT_TAGLINE_ZH}}` | Chinese tagline |
   | `{{PROJECT_TAGLINE_EN}}` | English tagline |
   | `{{PRODUCT_OWNER}}` | Owner name |
   | `{{TECH_STACK}}` | Tech stack description |
   | `{{DATE}}` | Date (YYYY-MM-DD) |
   | `{{CHANGELOG_ZH}}` | Version change note (Chinese) |
   | `{{CHANGELOG_EN}}` | Version change note (English) |

3. Replace section content marked with `<!-- REPLACE -->` comments.

4. Add the project card to `index.html` (PRD Hub home):
   ```html
   <a class="project-card" href="<project-name>/prd_v1.0.html">
     <div class="project-name">Project Name</div>
     <div class="project-desc">One-line description</div>
     <div class="project-meta">
       <span class="tag tag-mvp">v1.0 MVP</span>
       <span>Updated: 2026-03-27</span>
     </div>
   </a>
   ```

## Document Structure

The template follows a 10-section PRD standard:

1. **Project Info** — name, owner, tech stack, version history
2. **Background** — problems, why now
3. **Goals** — metrics table (goal type, description, metric, target)
4. **Users & Scenarios** — persona, user journey map
5. **Feature List** — modules with priority and status tags
6. **Detailed Design** — per-module: flow diagram + rules + prototype slice
7. **Flowcharts** — core user flow, data flow (Mermaid)
8. **Edge Cases** — error handling table
9. **Analytics** — event tracking table
10. **Roadmap** — phase timeline
11. **Appendix** — env vars, design system refs

## Features

### Theme Toggle (Light / Auto / Dark)
- Top-right button group
- Uses `data-theme` attribute on `<html>`
- CSS variables switch all colors
- Mermaid diagrams re-render on theme change
- Preference saved to `localStorage` (key: `prd-hub-theme`)

### Language Toggle (CN / EN)
- Top-right button group
- Uses `data-zh` and `data-en` attributes on elements
- `setLang('zh')` or `setLang('en')` switches all text

### Mermaid Diagrams
- Initialized with `theme: 'base'` + custom `themeVariables`
- Dark and light color palettes defined in `darkMermaid` / `lightMermaid` JS objects
- Re-renders on theme switch via `renderMermaid()` function
- Supports: `flowchart TD`, `sequenceDiagram`, `erDiagram`

### CSS Variables

All colors are controlled via CSS custom properties in `:root` (light) and `html[data-theme="dark"]` (dark). Key variables:

| Variable | Purpose |
|---|---|
| `--bg` | Page background |
| `--bg-card` | Card / section background |
| `--text` | Primary text |
| `--text-muted` | Secondary text |
| `--accent` | Accent color (links, active states) |
| `--border` | Borders and dividers |
| `--table-head` | Table header background |
| `--table-stripe` | Table even-row background |
| `--code-bg` / `--code-text` | Inline code styling |
| `--mermaid-bg` | Diagram container background |
| `--tag-mvp-bg` / `--tag-mvp-text` | Status badge colors |

## Adding a Mermaid Diagram

```html
<div class="mermaid">
flowchart TD
  A[Start] --> B{Decision}
  B -->|Yes| C[Action]
  B -->|No| D[Other Action]
</div>
```

The diagram will automatically use the correct color palette for the current theme.

## Version Management

When iterating to v1.1:
1. Copy `prd_v1.0.html` → `prd_v1.1.html`
2. Update version in the version bar `<select>`
3. Add changelog entry to the version history table
4. Never overwrite v1.0 — keep as historical snapshot
