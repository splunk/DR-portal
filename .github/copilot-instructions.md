# Copilot Instructions for DR‑Portal

These notes help AI coding agents work effectively in this repo. Keep changes minimal, consistent, and accessible.

## What This Repo Is
- Static multi‑page HTML portal (no build system) showcasing Cisco + Splunk demos across: AI/ML, Security, Observability, BI, Platform.
- Each domain has a hub page (e.g., `ai.html`) and several detail pages (e.g., `ai1.html`..`ai4.html`).
- Content is self‑contained per page with inline CSS for portability.

## Key Files/Patterns
- Reused classes: `.wrap`, `.grad`, `.card`, `.shot`, `.frame`, `.corner-img`, `.back`.
- Color tokens: `--o`, `--p`, `--v`, `--text` (see examples in pages).
- Back navigation uses a JS helper that avoids stepping iframe history: `smartBack(fallback)` as in `ai1.html`.
- Inactivity redirect appears on some detail pages (e.g., `ai1.html`): 10‑minute idle → `index.html`.

## Embeds (Navattic)
- Demos are embedded via `iframe` to `https://cisco-full-stack-observability.navattic.com/...` with:
  - `allow="fullscreen; autoplay; encrypted-media; clipboard-read; clipboard-write"`,
  - descriptive `title`,
  - `loading="lazy"` where appropriate,
  - wrapped in a `.frame` container (rounded corners + shadow).
- Pages currently embedding Navattic (17 total): `ai1.html`, `ai2.html`, `ai3.html`, `ai4.html`, `AIassistants1.html`, `AIassistants2.html`, `AIassistants3.html`, `bi.html`, `observability1.html`, `observability2.html`, `observability3.html`, `platform1.html`, `platform2.html`, `platform3.html`, `security1.html`, `security2.html`, `security3.html`.

## Fullscreen Pattern
- Example implementation in `ai1.html`:
  - Button near the top right with clear label/icon.
  - JS `toggleFullscreen()` calls `frame.requestFullscreen()` on the `.frame` wrapper.
  - Keyboard shortcut: press `f` to toggle.
- When adding fullscreen to other pages, copy the button + script block and adjust positioning to avoid overlapping `.corner-img`.

## Navigation & Cards
- Hub pages link to detail pages using `.card .shot` anchors with `target="_self"` and proper `alt` text on images.
- The `.back` button is a `<button>` invoking `smartBack('index.html')`; do not use `history.back()` (it can get stuck inside iframes).

## Local Preview / QA
- Open files directly or use a tiny server for iframe features:
  - PowerShell: `python -m http.server 8000; Start-Process http://localhost:8000/index.html`
- Quick checks per page: heading hierarchy, `iframe` `title`, focus styles (`:focus-visible`), alt text, mobile breakpoint at ~720px.

## Adding/Updating a Demo Page
1. Start from a similar existing page; keep inline CSS structure.
2. Place new images in `Assets/` and reference relatively.
3. For new iframes, include `title`, `allow` list above, and wrap in `.frame`.
4. Add/position `.corner-img` appropriately; keep it clickable to the hub or index.
5. If adding a fullscreen button, ensure mobile hides the text label to save space.

## Gotchas
- Keep styles minimal and consistent—avoid introducing a global stylesheet unless agreed.
- Use `window.top.location.replace(document.referrer)` in `smartBack` to avoid iframe session history loops.
- Do not rely on service workers or client routing—this is a purely static site intended for GitHub Pages / file preview.