# Working Notes — Colby Davis Personal Landing Page

> **Internal document — not intended for public audiences.**
> This file is for developer and AI assistant reference only. Update it at the end of every working session before closing the project.

---

## How to Use This File (For AI Assistants)

1. **Read this entire file before suggesting changes or writing any code.** Do not assume project state from the file tree alone.
2. **Read `README.md`** for the public-facing project description, tech stack table, and installation instructions.
3. **Do not change the folder structure or file naming conventions** without discussing the change here first and getting explicit approval.
4. **Follow all conventions listed in the Conventions section exactly** — including heading style, CSS naming, and commit message format.
5. **Do not suggest any approach listed in "What Was Tried and Rejected."** Those paths were deliberately abandoned.
6. **Ask clarifying questions before making large structural changes** — especially anything that would touch `index.html` layout order, the CSS variable system, or the responsive breakpoint strategy.
7. **This project was AI-assisted (Replit Agent / Claude).** All code was reviewed and approved by the author. Refactor conservatively — prefer targeted edits over rewrites. Do not restructure working sections unless there is a clear, stated reason.

---

## Current State

**Last Updated:** 2026-03-23

This is a complete, deployed static single-page personal landing page. All seven required sections are built and styled. The site passes Nu HTML Checker validation with zero errors or warnings. The design matches the spec in `STANDARDS.md` exactly.

### What Is Working

- [x] Sticky navigation bar with anchor links to all seven sections
- [x] Hero section — circular headshot, name, tagline, LinkedIn CTA, resume download button
- [x] About Me — dual BBA degrees, Entrepreneurial Management certificate, GPA 3.80, Dean's List, Iowa Flagship Award
- [x] Projects — two-column desktop grid / single-column mobile; all three projects with tool badges and bullet points
- [x] Skills — pill badges in two grouped categories (Financial & Data Tools, Programming)
- [x] Experience & Leadership — five entries with left-accent border cards
- [x] Resume section — PDF download button linked to `resume/colbydavis_resume.pdf`
- [x] Contact — email, LinkedIn, GitHub labeled icon links plus HTML form
- [x] Footer
- [x] Fully responsive: 320 px, 420 px, 680 px, and full desktop breakpoints
- [x] WCAG 2.2 AA: alt text, heading hierarchy, focus-visible styles, color contrast
- [x] All external links use `rel="noopener noreferrer"` and `target="_blank"`
- [x] Nu HTML Checker — zero errors, zero warnings
- [x] `README.md` — complete with badges, all 16 sections
- [x] `WORKING_NOTES.md` — this file

### What Is Partially Built

- [ ] **Contact form** — HTML structure is present and styled, but has no submission backend. A form service (Formspree or similar) needs to be connected for it to actually send messages.

### What Is Not Started

- [ ] Dark mode (`prefers-color-scheme` media query)
- [ ] Favicon
- [ ] Functional form backend (Formspree, Netlify Forms, etc.)
- [ ] GitHub pinned-repo widget
- [ ] Scroll-triggered animations (Intersection Observer API)
- [ ] `LICENSE` file on GitHub (needs to be added via GitHub UI — MIT)

---

## Current Task

**What I was working on when I last stopped:**
The landing page is fully built and validated. The most recent work was generating `README.md` and `WORKING_NOTES.md` as course deliverables. All code, content, and layout passed the Nu HTML Checker with zero issues after removing a redundant `role="navigation"` attribute from the `<nav>` element.

**The very next step is:**
Add a `LICENSE` file to the GitHub repository by going to the repo on GitHub → Add file → Create new file → name it `LICENSE` → choose MIT template. This will make the MIT license badge in `README.md` link correctly.

---

## Architecture and Tech Stack

| Technology | Version | Why It Was Chosen |
|---|---|---|
| HTML5 | Current standard | Required by `STANDARDS.md`; semantic elements improve accessibility and SEO |
| CSS3 (vanilla) | Current standard | Required by `STANDARDS.md`; no framework keeps the site lightweight and avoids dependency overhead |
| Google Fonts — Inter | Latest via CDN | Specified in `STANDARDS.md`; Inter is highly legible at small sizes and projects a modern, professional tone |
| Python 3 `http.server` | Bundled with Python 3 | Zero-dependency dev server for serving static files in the Replit environment on port 5000 |
| Nu HTML Checker | Online tool | W3C-standard HTML validation; used manually to confirm zero errors before submission |
| shields.io | Online badge service | Standard for GitHub README badges; no install required |

---

## Project Structure Notes

```
mod-8-landing-page/
├── index.html                  # Entire single-page site — all sections in one file
├── css/
│   └── stylesheet.css          # All styling; CSS custom properties at top; no inline styles anywhere
├── images/
│   └── colbydavis_headshot.jpg # Must stay at this exact path; referenced in index.html hero section
├── resume/
│   └── colbydavis_resume.pdf   # Copy of attached PDF; linked from hero and resume sections
├── attached_assets/            # Raw uploaded files from Replit; NOT served by the web server
│   └── Colby_Davis_Final_Resume_01-26-26_1774293152704.pdf
├── PRD.md                      # Product requirements; source of truth for required content
├── STANDARDS.md                # Technical and design standards; source of truth for visual rules
├── README.md                   # Public-facing documentation
├── WORKING_NOTES.md            # This file
├── replit.md                   # Replit environment notes (auto-maintained)
└── .github/
    └── workflows/              # Azure Static Web Apps CI/CD (pre-existing; not used in Replit)
```

**Non-obvious decisions:**
- `css/` is a dedicated folder (not inline styles) as required by `STANDARDS.md` folder structure spec.
- `resume/colbydavis_resume.pdf` is a copy of the original from `attached_assets/` because `attached_assets/` is not served by the dev web server.
- `images/colbydavis_headshot.jpg` is the exact filename referenced in `index.html` — do not rename it.

**Files that must not be changed without discussion:**
- `images/colbydavis_headshot.jpg` — filename and path are hard-coded in `index.html`
- `resume/colbydavis_resume.pdf` — filename and path are hard-coded in `index.html` (two locations)
- `css/stylesheet.css` — all CSS custom properties (`:root` block) define the design system; changing colors here affects the entire site

---

## Data / Database

This project has no persistent data, database, or backend. It is a fully static site. All content is hard-coded directly in `index.html`. There are no API calls, no local storage reads, and no cookies.

---

## Conventions

### Naming Conventions
- **HTML file:** `index.html` (lowercase, single file)
- **CSS file:** `css/stylesheet.css` (per `STANDARDS.md` folder spec)
- **CSS classes:** kebab-case (e.g., `.hero-inner`, `.project-card`, `.skill-badge`)
- **CSS custom properties:** kebab-case prefixed with `--` (e.g., `--accent`, `--section-gap`)
- **Image files:** lowercase with hyphens (e.g., `colbydavis_headshot.jpg`)
- **Section IDs:** single lowercase words matching the nav link text (e.g., `#hero`, `#about`, `#projects`)

### Code Style Rules
- No inline styles anywhere — all styles in `css/stylesheet.css`
- No JavaScript — this is a static site per `STANDARDS.md`
- No external CSS frameworks — vanilla CSS only
- HTML entities for special characters (e.g., `&amp;`, `&mdash;`, `&middot;`)
- All external `<a>` tags must include `target="_blank" rel="noopener noreferrer"`
- Semantic HTML5 elements throughout: `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- Every `<img>` must have a descriptive `alt` attribute

### CSS Patterns
- CSS custom properties (`:root` block) define all colors, spacing, and sizing — do not hard-code color hex values outside of `:root`
- Mobile-first: base styles target all sizes; `@media (max-width: ...)` overrides adjust downward
- Breakpoints: 680 px (tablet), 420 px (small mobile), 360 px (narrow mobile)
- Section alternation: white sections use default `--bg`; alternate sections add `.section-alt` class which applies `--secondary-bg`

### Git Commit Message Style
- Imperative mood, present tense (e.g., "Add contact form", "Fix nav role warning")
- Prefix with action word: `Add`, `Fix`, `Update`, `Remove`, `Refactor`
- Keep subject line under 72 characters
- No trailing period

---

## Decisions and Tradeoffs

- **Decision made: Single `index.html` file for all sections.** The PRD and STANDARDS.md both specify a single-page architecture. Splitting into multiple HTML files would break anchor-link navigation and violate scope.
- **Decision made: No JavaScript.** STANDARDS.md explicitly states "No JavaScript or backend." The sticky nav, smooth scroll, and pill badges are all achieved with CSS and native HTML behavior only.
- **Decision made: Vanilla CSS with custom properties instead of a framework.** Required by STANDARDS.md. This also keeps the file portable, readable, and free of build tooling.
- **Decision made: Third project card (Regression Analysis) is a regular two-column grid item, not forced full-width.** An earlier version forced it full-width with `grid-column: 1 / -1`; this was removed after code review flagged it as inconsistent with the "two-column desktop grid" spec.
- **Decision made: Resume PDF copied to `resume/` subfolder.** `attached_assets/` is not served by the Replit web server, so the PDF had to be copied to a publicly-accessible path. The copy is the canonical file for download links.
- **Decision made: Nav stacks vertically below 360 px.** At very narrow widths (320–360 px), a single-row sticky nav with six links was too crowded. The nav breaks into two rows (brand + links) at this breakpoint to maintain readability without horizontal overflow.
- **Decision made: Inter font loaded via Google Fonts CDN `<link>` tag.** No local font files — keeps the repo lean and ensures the latest optimized font version is always served.

---

## What Was Tried and Rejected

- **`role="navigation"` on the `<nav>` element.** The `<nav>` element already has an implicit ARIA role of `navigation`. Adding it explicitly triggers a Nu HTML Checker warning. Removed — do not re-add this attribute.
- **Forcing the third project card to span full width (`grid-column: 1 / -1`).** Initially implemented to visually distinguish the Regression Analysis project, but flagged as inconsistent with the two-column grid spec. Removed — the three cards now follow uniform two-column flow on desktop.
- **Inline styles for one-off adjustments.** Not used anywhere — STANDARDS.md prohibits inline styles. All adjustments go in `stylesheet.css`.

---

## Known Issues and Workarounds

- **Contact form does not submit.** The `<form>` has `action="#"` and no backend. There is no workaround in place — it is intentionally inert for the static-site scope. To fix: replace `action="#"` with a Formspree endpoint URL and add `method="post"`. Do not remove the form HTML — it is required by the PRD and looks correct visually.
- **Resume PDF committed to Git.** Binary files in Git increase repository size over time. No workaround — accepted trade-off for simplicity at this project scale. If the PDF is updated, replace `resume/colbydavis_resume.pdf` with the new file.

---

## Browser / Environment Compatibility

**Tested browsers:**
- Google Chrome (latest) — fully functional
- Replit in-browser preview (Chromium-based) — fully functional

**Expected to work:**
- Firefox (latest) — CSS Grid, custom properties, and `position: sticky` are all well-supported
- Safari (latest) — same support profile; `object-fit: cover` on the headshot is broadly supported
- Edge (latest) — Chromium-based; behavior identical to Chrome

**Known incompatibilities:**
- Internet Explorer — not supported; CSS custom properties and Grid are not available in IE11. Not a concern for the recruiter audience.

**Development environment:**
- Platform: Replit (NixOS, `stable-25_05` channel)
- Runtime: Python 3 `http.server` on port 5000, bound to `0.0.0.0`
- No build step required — files are served directly

---

## Open Questions

- Should the contact form be wired to a real submission endpoint (e.g., Formspree) before final submission, or is the static HTML form sufficient for the course deliverable?
- Is a favicon required for the course grading rubric?
- Should the `attached_assets/` folder be deleted from the repository before making it fully public, to avoid publishing the raw uploaded files?
- Is a `LICENSE` file required by the course rubric, or is the README badge and statement sufficient?

---

## Session Log

### 2026-03-23
- Built complete `index.html` with all seven sections using real resume and PRD content
- Built `css/stylesheet.css` with full design system (custom properties, responsive breakpoints, all components)
- Copied resume PDF from `attached_assets/` to `resume/colbydavis_resume.pdf`
- Fixed Nu HTML Checker warning: removed redundant `role="navigation"` from `<nav>` element
- Removed forced full-width override on third project card after code review
- Added narrow-screen nav stacking breakpoint at 360 px
- Generated complete `README.md` with all 16 sections and correct badge URLs
- Generated `WORKING_NOTES.md` (this file)
- Left incomplete: contact form is inert (no submission backend); favicon not added; LICENSE file not yet created on GitHub
- Decisions: single-file architecture, no JS, vanilla CSS, PDF copied to `resume/` subfolder
- Next step when resuming: add MIT LICENSE file on GitHub via the web UI

---

## Useful References

- [MDN HTML5 element reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element) — semantic element usage
- [MDN CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties) — `:root` variable system
- [MDN CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout) — project card two-column grid
- [MDN `position: sticky`](https://developer.mozilla.org/en-US/docs/Web/CSS/position#sticky_positioning) — sticky navigation bar
- [Google Fonts — Inter](https://fonts.google.com/specimen/Inter) — font used throughout
- [Nu HTML Checker](https://validator.w3.org/nu/) — W3C HTML validation tool used for QA
- [shields.io](https://shields.io/) — badge generation for README
- [WCAG 2.2 Quick Reference](https://www.w3.org/WAI/WCAG22/quickref/) — accessibility standards followed
- [read.cv](https://read.cv) and [brittanychiang.com](https://brittanychiang.com) — design references cited in `STANDARDS.md`
- AI assistance: Replit Agent (Claude) was used to scaffold the initial HTML/CSS structure. All content, decisions, and final output were reviewed and approved by the author.
