# DR-portal — Digital Resilience Portal (static site)

A small static HTML showcase that demonstrates Cisco + Splunk integration demos across several domains:
- Business Intelligence (BI)
- Security
- Observability
- AI / ML
- Platform Services

This repository contains a set of standalone HTML pages that act as a navigable demo portal. The site is intentionally simple (no build system) so it can be previewed directly from the filesystem or a lightweight static server.

## Quick preview (local)

Open pages directly in your OS default browser (Windows PowerShell):

```powershell
Start-Process .\index.html
```

Or run a tiny HTTP server and browse from http://localhost:8000:

```powershell
# from the repository root
python -m http.server 8000
Start-Process http://localhost:8000/index.html
```

Tip: use the server approach when testing iframe behavior or when some browsers restrict file:// access for certain features.

## Project structure

Top-level files (representative):
- `index.html` — landing page
- `ai.html`, `ai1.html`..`ai4.html`, `AIassistants*.html` — AI domain pages
- `security.html`, `security1.html`..`security3.html` — Security domain pages
- `platform.html`, `observability.html`, `bi.html` — other domain pages
- `Assets/` — local images and icons used across pages (background, thumbnails, SVGs, PNGs)
- `.github/copilot-instructions.md` — project notes/instructions for Copilot/AI coding agents

Notes:
- Pages embed external demos via iframes (navattic / cisco demo URLs).
- Fonts are loaded from Google Fonts (Lexend).
- The site intentionally uses inline styles inside each HTML file rather than a centralized CSS file to keep pages portable and self-contained.

## Conventions and patterns

- CSS variables are used across pages for consistent color tokens (examples: `--o`, `--p`, `--v`).
- Common classes repeated across pages: `.wrap`, `.grad`, `.frame`, `.shot`, `.card`, `.corner-img`, `.back`.
- Decorative corner thumbnails live in `Assets/` and are positioned with the `.corner-img` rule.
- Many pages use a gradient border technique implemented with `-webkit-mask` and `mask`. To maximize compatibility the code includes both `-webkit-mask` and `mask` properties.

## Accessibility & QA notes

- Some accessibility work was started (focus-visible rules, alt text, and ARIA on interactive cards), but a repository-wide accessibility audit is pending.
- Recommended quick checks:
  - Ensure each `img` has meaningful `alt` text (decorative-only images should use empty `alt=""`).
  - Verify keyboard navigation (tab order) across interactive cards and the back link.
  - Confirm `iframe` titles are descriptive.

## Recent housekeeping performed

- All PNG/SVG assets were moved to `Assets/` and HTML pages were updated to reference local assets instead of raw GitHub URLs.
- A missing CSS brace and `mask` compatibility lines were fixed on pages where visual issues were observed.
- Corner thumbnail styling was unified across pages (responsive width, border-radius, shadow, object-fit).

## Next recommended steps

1. Run a full accessibility pass across all pages and fix missing `alt` text / ARIA labels.
2. Remove any remaining debug/test snippets (search for `console.log`, debug anchor links, or commented-out scripts).
3. (Optional) Centralize repeating CSS into a single `styles.css` and update pages to reference it to simplify maintenance.
4. Consider a lightweight preview workflow (npm script or PowerShell alias) if you preview locally often.

## Contributing

Small changes are welcome. Please follow these rules:
- Keep pages self-contained unless moving to a shared stylesheet is agreed.
- When adding assets, place them in `Assets/` and reference them with relative paths.

If you'd like, I can:
- run a repo-wide search and replace to ensure no remaining remote image URLs exist,
- perform the accessibility sweep and open PR-ready fixes,
- extract shared CSS to a single file and update pages.

---
Generated / updated by the repository maintainer tools on request. For questions, see the project owner or open an issue.
