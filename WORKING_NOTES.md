# Working Notes — miamaiers-landing-page

> This is an internal working document intended for developer and AI assistant reference only. It is not a public-facing document. Update this file at the end of every working session.

---

## How to Use This File (For AI Assistants)

1. Read this entire file before suggesting changes or writing code.
2. Read `README.md` for the public-facing project description.
3. Do not change the folder structure or naming conventions without explicit discussion and approval.
4. Follow all conventions listed in the Conventions section exactly.
5. Do not suggest any approach listed in the "What Was Tried and Rejected" section.
6. Ask clarifying questions before making large structural changes.
7. This project was vibe coded with Claude (AI-assisted). Refactor conservatively — do not rewrite working code unless there is a clear, specific reason.

---

## Current State

**Last Updated:** 2026-03-12

The site is fully built, functional, and deployed on Replit. All five content sections (Hero, About, Skills, Projects, Contact) are complete with real content sourced from Mia's resume and PRD. The design matches the approved cream/rose/white palette with DM Sans typography. The README and supporting documentation are finalized.

### What Is Working

- [x] Hero section with circular headshot, name, tagline, and subtitle
- [x] About section with academic standing, career details, and extracurricular role
- [x] Skills section with two groups — Tools (accent pills) and Analytical Techniques (secondary pills)
- [x] Three project cards with descriptions and technology tags
- [x] Contact section with LinkedIn, GitHub, and email icon badges
- [x] Sticky navigation bar with smooth-scrolling anchor links
- [x] Responsive layout at 320px, 480px, 600px, 768px, and 1024px+
- [x] WCAG 2.2 Level AA compliance (contrast, heading hierarchy, alt text, keyboard nav)
- [x] External links open in new tab with `rel="noopener noreferrer"`
- [x] Python HTTP server running on port 5000
- [x] Static deployment configured on Replit
- [x] README.md with 16 sections, badges, and real content
- [x] PRD.md and STANDARDS.md documentation in place

### What Is Partially Built

- [ ] Favicon — no favicon file exists; browser tab shows a generic icon
- [ ] Open Graph meta tags — not added; shared links will show no preview image or description
- [ ] Smooth scroll anchor offset — `scroll-behavior: smooth` is set in CSS but the sticky nav bar overlaps the target heading when clicking anchor links

### What Is Not Started

- [ ] `LICENSE` file in the repository root (README references it but it does not exist)
- [ ] Dark mode toggle
- [ ] Blog or case study section
- [ ] Live project demo embeds
- [ ] Page analytics integration
- [ ] Downloadable resume button (PDF generated from site content)

---

## Current Task

**What I was working on when I last stopped:** Generating the `WORKING_NOTES.md` internal reference document. All site content, styling, and documentation (README, PRD, STANDARDS) are complete. The last code changes were correcting the repository name from `miamaiers-personal-landing-page` to `miamaiers-landing-page` across the README.

**The very next step is:** Create the `LICENSE` file in the repository root (MIT License) so the README's license link resolves correctly.

---

## Architecture and Tech Stack

| Technology | Version | Why It Was Chosen |
|---|---|---|
| HTML5 | Living Standard | Required by BAIS 3300 assignment; semantic elements provide accessibility and SEO structure |
| CSS3 | Living Standard | Required by assignment; vanilla CSS chosen over frameworks to keep the project simple and dependency-free |
| Google Fonts (DM Sans) | Variable font, weights 300–700 | Chosen by the user for its professional, readable appearance; loaded via CDN with `preconnect` for performance |
| Python 3 (`http.server`) | 3.x (system default) | Lightweight built-in dev server; no install needed; serves static files on port 5000 |
| Git / GitHub | Latest | Version control and repository hosting; required for BAIS 3300 submission |
| Replit | Cloud IDE | Development environment and static hosting; provides instant deployment without separate server setup |

---

## Project Structure Notes

```
miamaiers-landing-page/
├── index.html              # Single-page site with all 5 content sections
├── css/
│   └── stylesheet.css      # All styles, CSS variables, responsive breakpoints
├── js/
│   └── scripts.js          # Empty — exists only to satisfy folder structure requirement
├── images/
│   └── headshot.jpeg       # Professional headshot (160px circular crop in hero)
├── PRD.md                  # Product requirements document (content spec)
├── STANDARDS.md            # Technical and design standards (rules for AI/dev)
├── README.md               # Public-facing project documentation (16 sections)
└── WORKING_NOTES.md        # This file — internal developer/AI reference
```

- `js/scripts.js` is intentionally empty. The BAIS 3300 assignment requires the `/js/` folder to exist with a `scripts.js` file, but the site uses no JavaScript. Do not add JS unless explicitly requested.
- `images/headshot.jpeg` is the only image. The STANDARDS.md forbids external image URLs — all images must be local in `images/`.
- `STANDARDS.md` contains template-style bracketed placeholders (e.g., `[e.g., #f7f0ca]`) from the original assignment template. These are reference scaffolding, not values to implement. The actual values are defined in CSS custom properties in `stylesheet.css`.
- Do not change the folder structure without discussion. The `/css/`, `/js/`, and `/images/` subfolder layout is a graded assignment requirement.

---

## Data / Database

This project has no persistent data, no database, and no back-end. It is a fully static site consisting of a single HTML file, one CSS file, and one image. All content is hardcoded in `index.html`.

---

## Conventions

### Naming Conventions

- **Files:** Lowercase with hyphens for multi-word names (e.g., `stylesheet.css`, `headshot.jpeg`)
- **CSS classes:** Lowercase with hyphens, BEM-inspired but not strict BEM (e.g., `.project-card`, `.tag-accent`, `.hero-tagline`, `.nav-links`)
- **HTML IDs:** Lowercase with hyphens, used for anchor links and `aria-labelledby` associations (e.g., `id="about-heading"`, `id="project-blotter"`)
- **CSS custom properties:** Prefixed by role — `--color-*` for colors, `--font-*` for typography, `--radius-*` for border radius, `--max-width` for layout (e.g., `--color-accent`, `--radius-pill`)

### Code Style Rules

- No inline `style=""` attributes anywhere
- No `<style>` tags in HTML — all CSS lives in `css/stylesheet.css`
- CSS is organized in labeled sections using `/* === SECTION NAME === */` comment blocks
- HTML uses 2-space indentation
- CSS uses 2-space indentation
- All `<img>` elements require descriptive `alt` attributes
- All external links use `target="_blank"` with `rel="noopener noreferrer"`
- The `mailto:` link does not use `target="_blank"` (opens in the user's email client)

### Framework-Specific Patterns

- No framework is used. This is vanilla HTML5 + CSS3.
- CSS custom properties (`:root` variables) are used for all colors, fonts, spacing, and radii so the palette can be changed in one place.
- Responsive design uses three `@media` breakpoints: `max-width: 480px` (mobile), `min-width: 600px` (tablet), `min-width: 800px` (desktop).
- Alternating section backgrounds use the `.section-alt` class to apply `--color-surface` background.

### Git Commit Message Style

- Imperative mood, present tense (e.g., "Fix repository name in README")
- First line: short summary (50 characters or fewer when possible)
- Body (if needed): blank line after summary, then details wrapped at 72 characters

---

## Decisions and Tradeoffs

- **Vanilla CSS over Bootstrap/Tailwind:** The project is small enough that a framework adds unnecessary complexity. Vanilla CSS keeps the file count low and avoids CDN dependencies beyond Google Fonts. Do not suggest reversing this.

- **DM Sans as the sole typeface:** User explicitly chose DM Sans for both headings and body after reviewing options. It is loaded as a variable font (weights 300–700) via Google Fonts CDN with `preconnect`. Do not suggest reversing this.

- **Cream/rose/white color palette (#FAF8F5 background, #A8405E accent, #FDE8EF light accent):** User chose this over navy/dark themes and deeper cream tones. The palette is defined in CSS custom properties. Do not suggest reversing this.

- **Max content width of 800px:** Keeps the single-column layout readable and focused, consistent with reference sites (read.cv, brittanychiang.com). Do not suggest reversing this.

- **No JavaScript:** The site is intentionally static HTML + CSS. The `js/scripts.js` file exists only for the assignment folder structure requirement. Do not add JavaScript unless explicitly asked.

- **No resume PDF link:** STANDARDS.md and PRD.md both explicitly prohibit linking to or embedding a static PDF resume. Do not suggest reversing this.

- **Inline SVG icons for contact links:** LinkedIn, GitHub, and email icons are inline SVGs rather than icon font libraries or external image files. This avoids extra HTTP requests and allows CSS `currentColor` styling for hover effects. Do not suggest reversing this.

- **Hero padding reduced to 40px top / 48px bottom:** User explicitly requested less whitespace above the hero. Mobile breakpoint uses 28px top / 36px bottom. Do not suggest reversing this.

- **Contact intro text:** User specified the exact phrasing: "I am always open to connect and welcome anyone to reach out." Do not change this without explicit approval.

- **Aflac project tags: Power BI, Data Modeling, AI Interventions:** User explicitly changed the first tag from "Forecasting" to "Power BI." Do not suggest reversing this.

- **Two tag color variants:** `.tag-accent` (dark rose background, white text) for tools and technology tags; `.tag-secondary` (light pink background, dark rose text) for analytical technique tags in the Skills section. Do not suggest reversing this.

---

## What Was Tried and Rejected

- **Deeper cream background color (darker than #FAF8F5):** Tried a warmer/darker cream. User disliked it and reverted to the original #FAF8F5. Do not suggest a darker background.

- **"Forecasting" as the first tag on the Aflac Churn Project card:** Was originally "Forecasting" but user changed it to "Power BI." Do not use "Forecasting" for the Aflac card.

- **Italicized template guidance hints in README.md:** Tried adding italic lines under each README section heading (e.g., "*A short paragraph explaining...*") as template hints. These were rejected as looking like placeholder text. Do not add them back.

- **Navy/dark color scheme:** User explicitly chose cream/pink/white and rejected any dark or navy palette. Do not suggest dark mode as a default; it can only be offered as an optional toggle.

- **Hero top padding of 80px:** Was originally 80px. User found it too spacious and reduced it to 40px (28px on mobile). Do not increase hero top padding.

---

## Known Issues and Workarounds

- **Smooth scroll anchor offset:** When clicking a nav link (e.g., "About"), the browser scrolls to the section heading but the sticky nav bar overlaps the top of the heading. No workaround is in place. A future fix would use `scroll-margin-top` on section elements set to the nav bar height.

- **No favicon:** The browser tab shows a generic icon. No workaround is in place. A favicon file needs to be created and linked in `<head>`.

- **No Open Graph meta tags:** When the site URL is shared on LinkedIn or other social platforms, no preview image or description will appear. No workaround is in place.

- **Duplicate `@media (min-width: 800px)` rule:** The 800px breakpoint in `stylesheet.css` repeats the same `grid-template-columns: 1fr 1fr` rule already set at 600px. It is harmless but redundant. Do not remove it without discussion — it may be a placeholder for future desktop-only styles.

- **STANDARDS.md contains unfilled template placeholders:** The color palette table and typography section still show `[e.g., #f7f0ca]`-style bracketed hints from the original assignment template. These do not affect the site — the actual values are in `stylesheet.css` CSS custom properties. The placeholders are left in place because STANDARDS.md is an assignment deliverable.

---

## Browser / Environment Compatibility

**Tested browsers:**
- Google Chrome (latest) — fully functional
- Mozilla Firefox (latest) — fully functional
- Safari (latest) — fully functional

**Expected to work:**
- Any modern browser supporting CSS custom properties, flexbox, and CSS grid (all evergreen browsers)

**Known incompatibilities:**
- Internet Explorer — not supported (CSS custom properties and grid are not available)
- Browsers without `scroll-behavior: smooth` support will still function; anchor links will jump instantly instead of scrolling

**Development environment:**
- Replit (NixOS-based Linux container)
- Python 3 `http.server` module on port 5000
- Static deployment configured on Replit

---

## Open Questions

- Should a `scroll-margin-top` value be added to section elements to offset the sticky nav bar height when anchor links are clicked?
- Should a favicon be a simple monogram ("MM") or a more branded icon?
- What image and description should be used for Open Graph meta tags when the site is shared on social media?
- Should a dark mode toggle be added, and if so, should it default to light or follow the system preference?
- Should a blog or case study section be added to the site, and if so, should it be a separate page or additional sections on the single page?
- Should live project demo embeds (dashboards, notebooks) be added to the project cards, and if so, what format should they use?

---

## Session Log

### 2026-03-12

- Built the complete single-page landing site: Hero, About, Skills, Projects (3 cards), and Contact sections with real content from resume and PRD
- Created `css/stylesheet.css` with CSS custom properties, responsive breakpoints at 480px/600px/800px, and WCAG 2.2 AA compliant design
- Applied iterative user-requested tweaks: reduced hero top padding (80px to 40px), changed Aflac tag from "Forecasting" to "Power BI", updated contact intro text, reverted background to #FAF8F5
- Generated 16-section README.md with shields.io badges (HTML5, CSS3, Google Fonts, MIT, Vibe Coded), tech stack table, file tree, changelog, and acknowledgements
- Corrected repository name from `miamaiers-personal-landing-page` to `miamaiers-landing-page` in all four README occurrences
- Generated this WORKING_NOTES.md internal reference document
- Left incomplete: favicon, Open Graph tags, scroll offset fix, LICENSE file
- Decisions made: vanilla CSS only, DM Sans font, cream/rose palette, no JS, no resume PDF link, inline SVG icons
- Next step when resuming: create the MIT LICENSE file so the README link resolves

---

## Useful References

- [DM Sans on Google Fonts](https://fonts.google.com/specimen/DM+Sans) — the typeface used throughout the site
- [shields.io](https://shields.io/) — badge generator used for README badges
- [WCAG 2.2 Quick Reference](https://www.w3.org/WAI/WCAG22/quickref/) — accessibility guidelines followed for Level AA compliance
- [read.cv](https://read.cv/) — reference site for overall simplicity and whitespace (per STANDARDS.md)
- [brittanychiang.com](https://brittanychiang.com/) — reference site for section hierarchy, light background only (per STANDARDS.md)
- [CSS `scroll-margin-top`](https://developer.mozilla.org/en-US/docs/Web/CSS/scroll-margin-top) — potential fix for the sticky nav anchor offset issue
- [Open Graph Protocol](https://ogp.me/) — specification for social media link preview meta tags
- AI tools used: Claude (Anthropic) was used for initial code generation and iterative refinement. All output was reviewed and modified by the author.
