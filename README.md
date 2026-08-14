# agents2.app

Personal AI and cloud portfolio site for Baba Shaik, Principal Cloud Architect. Static site, no build step, hosted on GitHub Pages at [agents2.app](https://agents2.app).

## Structure

| File | Purpose |
|---|---|
| `index.html` | Homepage markup. Loads and renders `projects.json` client-side (see the `loadProjects()` script at the bottom of the file). |
| `styles.css` | All site styling — CSS custom properties for the color/gradient theme live at the top in `:root`. |
| `projects.json` | Single source of truth for every project card and the "Currently working on" strip. Edit this and push to add, update, or remove a project — no HTML changes needed. |
| `assets/screenshots/` | Project screenshots referenced by `projects.json`. Missing files fall back to a "Screenshot coming soon" placeholder automatically. |
| `CNAME` | Required by GitHub Pages for the custom domain — contains `agents2.app`. Don't delete. |

## Homepage sections (top to bottom)

1. Sticky nav (About / Certifications / Projects / Archive / GitHub)
2. Hero — headshot photo, name, role line, summary, GitHub/LinkedIn links
3. "Currently working on" strip — auto-populated from `projects.json` entries with `status: "Active"`
4. About — career narrative + quick-facts grid
5. Certifications — grouped into Cloud & AI / Microsoft & AWS / Oracle Cloud Infrastructure
6. Active projects / Prototypes / Archive — all data-driven from `projects.json`
7. Footer

## `projects.json` schema

Each entry:

```json
{
  "name": "Project Name",
  "slug": "project-name",
  "description": "One or two sentences describing what it does and why it exists.",
  "tech": ["Python", "OCI"],
  "screenshot": "assets/screenshots/project-name.png",
  "github": "https://github.com/BfShaik/project-repo",
  "status": "Active"
}
```

`status` must be one of:
- `Active` — currently in progress, shown in the Active projects grid and the "Currently working on" strip
- `Prototype` — working experiment, shown in its own grid, not in the strip
- `Archived` — earlier project, shown as a compact row in the Archive list, not in the strip

## Adding a new project

1. Add a new object to `projects.json` following the schema above.
2. Drop a screenshot into `assets/screenshots/` matching the `screenshot` path in the entry (optional — safe to skip, the placeholder will show until it exists).
3. Commit and push to `main`. GitHub Pages rebuilds automatically, usually live within a minute.

## Hosting setup (already configured — reference only)

**GitHub Pages** — repo is named `BfShaik.github.io`, deployed from the `main` branch root. Settings → Pages has the custom domain set to `agents2.app` with Enforce HTTPS on.

**DNS at Namecheap** — Domain List → Manage `agents2.app` → Advanced DNS:
- Four A records, host `@`, pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- One CNAME record, host `www`, pointing to `BfShaik.github.io.`

## Local development

Clone and edit directly, no build step required:

```bash
git clone https://github.com/BfShaik/BfShaik.github.io.git
cd BfShaik.github.io
# open index.html directly in a browser to preview, or run a local server:
python3 -m http.server 8000
```

Push to `main` when ready — that's the entire deploy process.
