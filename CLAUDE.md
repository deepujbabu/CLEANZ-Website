# CLEANZ website — working notes

Persistent guidance for working on this site. Read before making changes.
Last updated: July 2026.

## Process rules (learned the hard way, avoid repeat rounds)

- Inspect the real markup/CSS before changing layout. Read the relevant HTML block and both `main.css` and `custom.css` rules that apply. Do NOT diagnose layout from a screenshot alone; confirm in the code first.
- Fix the root cause in one pass. Find the actual CSS/DOM reason before editing, then make the full fix rather than iterating one guess at a time.
- Diagnose before re-cropping images. Check dimensions with Python/PIL and view the file first. Most "photo looks wrong" issues were layout/CSS, not the image.
- Verify after editing: check CSS brace balance, confirm referenced assets exist, and reason through the effect (or render a mock) before declaring done.
- When a colour/style choice is subjective, show options with the visualize widget (buttons that call sendPrompt) instead of guessing.

## Environment quirks (important)

- Some original photos revert on disk. `assets/img/team/Atul.jpg` and `Deepu.jpg` were restored to their originals by the environment after edits. Do NOT overwrite original people photos in place. If a crop is needed, save under a NEW filename (e.g. `Name_sq.jpg`) and point the HTML at it — but note the user may prefer the untouched original, so ask first.
- Image caching: browsers cache by filename; edits may not show without a hard refresh (Cmd+Shift+R). A `?v=N` query or a new filename busts it.
- Do not download remote images via curl/requests (web-fetch policy). Ask the user to drop files into the connected folder (`/Users/dpu/Downloads/cleanz` was used for staff/faculty photos).
- File deletion needs the cowork delete permission (already granted for this folder).

## How this site is built

- Static BootstrapMade "OnePage" template. Single page: `index.html` (lowercase). Deployed at cleanz.coe.iith.ac.in via `CNAME` (GitHub Pages).
- All restyling lives in `assets/css/custom.css`, loaded AFTER `main.css` to override. Keep `main.css` untouched. Beware inline `<style>` blocks in the body (e.g. the Gallery block) — they override linked CSS.
- Footer shows a version; changes logged in `CHANGELOG.md` (semver, minor bump per change set). Current: v1.2.

## Current structure after cleanup (only what's used)

- Root: `index.html`, `CHANGELOG.md`, `CLAUDE.md`, `CNAME`, `assets/`.
- `assets/`: `css/` (main.css, custom.css), `js/` (main.js), `img/` (Gallery/, team/, team/staffs/, logo.png, favicon.png, apple-touch-icon.png), `vendor/`.
- Vendor libraries kept: `bootstrap`, `bootstrap-icons`, `aos` ONLY. Swiper, GLightbox, PureCounter, Isotope, imagesLoaded, php-email-form were removed (unused) along with their tags and the matching init code in `main.js`. Do not reference those libs.
- Removed: leftover template pages, all demo image folders, old hero/diagram PNGs, replaced photos, `forms/`, `assets/scss/`, `assets/docs/` (postdoc PDFs — user will supply new ones as needed).

## Team / faculty & staff cards (the layout that caused the most trouble)

- Photos forced to a uniform square with the PADDING-BOX trick, NOT `aspect-ratio` (which failed with `height:auto`):
  - `.team .team-member .member-img { position:relative; width:100%; height:0; padding-top:100%; overflow:hidden; }`
  - `.team .team-member .member-img img { position:absolute; inset:0; width:100%; height:100%; object-fit:cover; object-position:top center; }`
- Because the image is absolutely positioned it gives the card no intrinsic width, so the card MUST have `.team .team-member { width:100%; }` or cards collapse to the width of the name text (long names -> wide cards). This was the real cause of the "misaligned names / different card widths" bug.
- Faculty grid: `col-lg-3 col-md-6` (4 per row). Staff grid: `row-cols-2 row-cols-md-3 row-cols-lg-5` (5 per row), cols are `col d-flex align-items-stretch`.
- Names are charcoal, not the green link colour: `.team-member .member-info h4 a { color: var(--heading-color); }`.
- Faculty list currently: Saptarshi, Raja, Kishalay, Chandra, Narasimha, Dshee, Atul, Sayak, Venkat, Pritha, Deepu, Meenakshi, Vamsi (Gande Vamsi Vikram, Chemical), Praneeth (D. V. Sai Praneeth, Civil). Ashok removed. Staff: Abhishek (kept), Suma, Nagaraju, Mallesham, Dinesh.

## Design decisions already settled (don't re-litigate)

- DARK hero (chosen from options): background `#14232a`, soft floating brand-colour glows, gradient wordmark `linear-gradient(120deg,#8ACBD1,#C7E1BF,#C8C8D3)`, light kicker/tagline, glassy translucent Vision/Mission cards (white titles), teal scroll cue. Hero cards lift on hover (translateY), NOT scale (scale caused overlap).
- Hero kicker = small "A Joint Initiative Of" label above "IIT Hyderabad · Coal India Limited" (middle dot, brand-teal separator, NO × symbol).
- DARK footer to bookend the hero: `#14232a`, light text, light gradient "CLEANZ" text wordmark (the logo PNG is dark-green and does NOT read on dark, so footer uses text not image). Template hardcodes a green `.copyright` background via `--accent-color` — override to transparent. Footer is compacted (reduced padding) and has 4 columns summing to 12: About (col-lg-4), Quick Links (col-lg-2), External Links (col-lg-2), Contact (col-lg-4).
- Rest of the page is light. Section titles have a small teal->green->purple gradient accent bar. Subtle brand glows behind About/Research/Gallery/Contact (Contact glow is teal, not pink).
- About "dimensions" and Research are dynamic CARDS, not the old PNG diagrams. Research = 6 focus-area cards + a cross-cutting themes chip row (Novel Carbon Materials, Coal Liquefaction, Circular Economy & Waste Management, AI/ML Applications, Energy Efficiency & Conservation).
- Gallery captions: white title on a dark gradient overlay, dates in brand teal (was clip-art cyan `#00ffff` — removed).
- Contact: info-items are white cards with tinted teal-green icon circles; "Call Us" card is commented out until a phone number is available.
- Brand palette: Teal #8ACBD1, Green #C7E1BF, Dark Green #78B598, Light Purple #C8C8D3, Dark Purple #9382B8, Pink #E7A2C0, Red #DE626E, Yellow #F6C869. Interactive/link accent = deeper green `#3d8168`.
- No em/en dashes anywhere (user preference). Use commas, parentheses, or full stops. Designations use parentheses, e.g. "Project Associate (Admin)".

## Still pending (needs user content)

- New sections requested but not built: News/Events, Projects/Themes, Facilities/Partners.
- Contact phone is a placeholder; "Call Us" card commented out.
- Openings section is text-only; user will supply advertisement PDFs to link when available.
