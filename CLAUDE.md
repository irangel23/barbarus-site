# Barbarus Consulting site

Marketing site for Barbarus Consulting, plus hosted support/privacy pages for the
Workshop iOS app. Static HTML, no build step, no framework.

## Repo status

This folder is its own git repo, separate from the Workshop app repo it happens to
live inside on disk (Workshop's `.gitignore` excludes it). Remote:
`https://github.com/irangel23/barbarus-site.git`. Deployed via GitHub Pages —
`CNAME` points the custom domain `barbarusconsulting.com` at it. This sandbox can't
reach github.com, so commits happen locally here and the user pushes manually.

## Structure

- `index.html` — homepage
- `workshop/index.html` — Workshop app detail/marketing page
- `support/workshop/index.html` — Workshop app support page
- `privacy/workshop/index.html` — Workshop app privacy policy
- `assets/` — logo (light/dark SVG variants), grain texture (light/dark JPG),
  Workshop app icon (light/dark PNG)

Each page is a single self-contained `.html` file with inline `<style>` — same
single-file convention as the Workshop app itself. No CSS/JS build pipeline.

## Design system

Brand palette (documented in a comment at the top of `index.html`'s `<style>`):

- Tactical Slate Blue `#1F2E45` — dominant logo color, headlines, dark-mode surfaces
- Chiseled Steel `#B0B7BC` — accent lines, borders, muted text (on dark)
- Crisp Shield Gray `#F4F6F8` — primary background, light-mode surfaces
- Iron Obsidian `#121821` — body text, dark-mode background
- Signal Cyan `#00A8E8` — CTAs, links, active states, circuit-node glow

Target usage weight: ~60% neutral (Shield Gray / Iron Obsidian), ~30% Slate Blue,
~10% Signal Cyan. All pages support light/dark automatically via
`prefers-color-scheme`, driven by CSS custom properties (`--bg`, `--text`,
`--heading`, `--muted`, `--link`, `--card`, `--border`, `--accent`, `--accent-ink`)
defined in `:root` and re-defined in the dark-mode media query — new pages should
follow this same variable pattern rather than hardcoding colors. Background uses a
repeating grain texture image (`--grain`) for subtle paper-like texture, swapped
per color scheme. Logo and app-icon images swap light/dark variants via
`.logo-light` / `.logo-dark` classes toggled by the same media query.

## Working conventions (carried over from the Workshop app chat)

- Keep every page a single self-contained HTML file — no separate CSS/JS files.
- Verify HTML validity and contrast/accessibility before considering a page done.
- Commit finished work locally with a clear message; never push to GitHub without
  the user explicitly asking — they push themselves once they're happy with it.
- Ask before anything irreversible or production-facing (DNS/CNAME changes,
  anything that touches the live domain beyond a normal page edit).
- For any non-trivial multi-step task, use a task list to track progress.
- Keep responses concise and direct — minimal preamble, no unnecessary formatting.
