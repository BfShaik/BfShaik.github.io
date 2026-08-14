# Project context for Claude Code

This is Baba Shaik's personal AI/cloud portfolio site, live at https://agents2.app. Static HTML/CSS/JS, no framework, no build step, hosted on GitHub Pages from this repo's `main` branch. Every push to `main` auto-deploys — there is no separate deploy step.

## What this site is

A portfolio for Baba, a Principal Cloud Architect at Oracle with 25 years in enterprise IT/cloud, now focused on hands-on agentic AI work (MCP tooling, agent frameworks, OCI). The site's tone is calm and professional, not a sales/startup page — credibility-first, not hype-first.

## Files

- `index.html` — all page markup. Renders `projects.json` client-side via the `loadProjects()` script at the bottom.
- `styles.css` — all styling. Theme variables (colors, gradient, radius) are CSS custom properties at the top in `:root`.
- `projects.json` — source of truth for every project card and the "Currently working on" strip. See schema below.
- `assets/screenshots/` — project screenshots. A missing file automatically falls back to a "Screenshot coming soon" placeholder, so it's fine to add a project entry before the image exists.
- `CNAME` — contains `agents2.app`, required by GitHub Pages for the custom domain. Never delete or edit unless the domain changes.

## `projects.json` schema

```json
{
  "name": "Project Name",
  "slug": "project-name",
  "description": "One or two sentences.",
  "tech": ["Python", "OCI"],
  "screenshot": "assets/screenshots/project-name.png",
  "github": "https://github.com/BfShaik/project-repo",
  "status": "Active"
}
```

`status` is one of `Active` (shown in the Active grid + the "Currently working on" strip), `Prototype` (its own grid, not the strip), or `Archived` (compact row in the Archive list, not the strip).

## Visual theme

Gradient glow + glassmorphism look, added 2026-08-14 per Baba's request after reviewing AI-startup templates for inspiration, while keeping the portfolio structure calm rather than sales-page-y:

- Fixed radial-gradient glow (blue/purple, `--accent: #6d8cff` / `--accent-2: #b46bff`) behind the hero via `body::before`
- Gradient-clipped `<h1>` name text
- Glass-panel cards (translucent background + `backdrop-filter: blur()`) for About facts, certification groups, project cards, and the archive list
- Card hover = lift + colored glow shadow, not a flat border-color change

## Hero photo

The headshot is embedded directly in `index.html` as a base64 `data:image/jpeg;base64,...` URI on the `<img class="avatar">` tag — not a separate file in `assets/`. This was a workaround for a now-irrelevant constraint (the previous editing environment couldn't upload binary files); there's no reason to keep doing it this way going forward. If the photo ever needs to change, it's simpler to save it as a normal file (e.g. `assets/headshot.jpg`) and point `src` at that path instead of re-encoding to base64 — much easier to review in diffs and edit locally.

Current caption: "25 years in enterprise IT and cloud. Now all-in on agentic AI." (`.avatar-caption`, italic, under the photo).

## Style/voice notes for future copy edits

Baba has iterated on hero copy a few times and prefers: clean two-sentence structure over comma-spliced run-ons, leading with credibility (title/years of experience) before the current focus, and avoiding corporate-brochure phrasing. When suggesting copy, offer 3-4 short options with a clear recommendation rather than one take-it-or-leave-it version.

## Known minor cleanup item

`index.html` currently ends with a duplicated `</html>` closing tag (harmless — browsers ignore it — but worth a one-line fix whenever the file is touched next).

## Hosting / DNS (reference, shouldn't need to change)

GitHub Pages serves from `main` branch root. Custom domain `agents2.app` is configured in Settings → Pages with Enforce HTTPS on. DNS lives at Namecheap (Advanced DNS): four A records for `@` → GitHub Pages IPs (185.199.108.153/.109.153/.110.153/.111.153), one CNAME for `www` → `BfShaik.github.io.`
