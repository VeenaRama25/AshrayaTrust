## Purpose
Short, focused guidance to help AI coding agents be immediately productive in this repository (a small static website).

## Project snapshot (what this repo is)
- A static, multi-page HTML site. Key files in the repo root: `index.html`, `about.html`, `contact.html`, `style.css`, `CNAME`, and image assets (stored in `asserts/`, e.g. `asserts/Ashraya Trust Logo.jpg`, `asserts/Ashraya.png.png`, `asserts/dummy.jpg`).
- No build system (no `package.json`, no bundler). There is no server-side code in the repository.

## Big picture / architecture
- All pages are plain HTML that include `style.css` via a relative link in the `<head>`. There is no client-side JS or API layer in the repo.
- Navigation uses simple relative links (e.g. `<a href="about.html">About Us</a>`). Keep links relative and use existing filenames unless you update all references.
- `CNAME` indicates this site is published with a custom domain (likely GitHub Pages). Do not remove or unintentionally change the `CNAME` file when making deploy changes.

## Developer workflows & quick commands
- Preview locally (PowerShell):
```powershell
python -m http.server 8000
# then open http://localhost:8000/
```
- The repo is ready for direct static hosting (GitHub Pages). There is no test suite or build step.

## Conventions & repository-specific gotchas
- Filenames contain spaces and duplicate extensions (example: `Ashraya Trust Logo.jpg`, `Ashraya.png.png`). When changing or renaming assets, update all references in HTML. Prefer using hyphenated, lower-case names for new assets to avoid URL-encoding issues.
- The contact form in `contact.html` has no `action` attribute and therefore no backend handling in this repo. If implementing form submissions, either:
  - Add a backend service and set `action`/`method` accordingly, or
  - Wire the form to a third-party form service (e.g. Formspree) and update the `<form>` tag and `button` handling.
- The footer is positioned `fixed` in `style.css`. Adding long content or modal UI may require changing footer positioning to avoid overlap.

## Integration points and recommended edits
- Adding analytics or external scripts: edit the `<head>` of each HTML file (or add a common include if you introduce templating). There is currently no JS folder; place new scripts at repo root or add a `js/` directory and reference them before `</body>`.
- To add a new page, create `yourpage.html`, link it in each header `<nav>`, and copy the existing header/footer structure to keep consistent navigation.

## Example tasks (how to implement common changes)
- Add a new page and nav link: copy `about.html` → `programs.html`, update title and content, then add `<a href="programs.html">Programs</a>` to each `nav` block.
- Enable contact form submissions (Formspree example):
  - Change the form tag in `contact.html` to `<form action="https://formspree.io/f/your-id" method="POST">` and leave inputs as-is.

## PR checklist for AI-generated changes
- Run the local server and verify pages render at `http://localhost:8000/`.
- Confirm relative links work (click header nav links).
- Verify any renamed assets are updated across HTML files.
- Preserve or explicitly update `CNAME` only when a domain change is intentional.
- Check mobile viewport meta tag is present (`<meta name="viewport" ...>` already in each page).

## Where to look for examples
- `index.html`, `about.html`, `contact.html` — page structure and navigation examples.
- `style.css` — global styling; note footer `position: fixed` and nav link styles.
- `CNAME` — custom domain configuration for GitHub Pages.

If anything above is unclear or you need more examples (form backend wiring, renaming assets safely, or converting to a templated site), tell me which area to expand and I'll update these instructions.
