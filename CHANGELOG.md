# Changelog

All notable changes to the CLEANZ website are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.3] - 2026-07-24

### Added

- New "Groundbreaking Ceremony" carousel in the Gallery section (dated 27th April 2026), with four photos stored in `assets/img/Gallery/2026/` as `Groundbreaking_1.jpeg` to `Groundbreaking_4.jpeg`.

## [1.2] - 2026-07-23

### Added

- New `assets/css/custom.css` applying a minimal, Apple-style restyle over the template, using the CLEANZ brand palette and an Avenir-first font stack.
- Replaced the two static diagram images with dynamic card layouts: the About "dimensions" graphic is now six animated brand cards, and Research is now six numbered focus-area cards plus a chip row of cross-cutting themes.
- Cohesive, subtle brand theming across sections: soft brand glows behind About, Research, Gallery and Contact; a small gradient accent bar under each section title; and a brand strip across the top of the footer.
- Open Graph and Twitter meta tags for richer link previews when the site is shared.
- Lazy-loading on team and gallery images for faster initial load.

### Changed

- Hero redesigned as a clean white, typographic layout with a gradient-filled wordmark, an eyebrow tag, soft floating brand-colour glows, and a scroll cue, replacing the clip-art background image.
- Research section rebuilt as a grid of icon cards (one per topic) instead of plain bullet lists; research and about diagrams enlarged.
- Footer now uses the CLEANZ logo image and a short blurb instead of plain text.
- Renamed `Index.html` to `index.html` so it resolves correctly on case-sensitive hosting (e.g. GitHub Pages).

- Enlarged the CLEANZ logo in the header.
- Updated the Staff list: refreshed P. Naga Suma, and added Machkuri Nagaraju, Bandari Mallesham, and Nagavamshi Dinesh Kumar with photos and contact emails.

### Removed

- Staff card for Ms. Ashwini Kale.
- Project cleanup: deleted unused BootstrapMade template pages (portfolio-details, service-details, starter-page), unused images and demo folders (clients, masonry-portfolio, portfolio, testimonials, old hero/diagram PNGs), replaced people photos, and junk/system files.
- Trimmed unused vendor libraries (Swiper, GLightbox, PureCounter, Isotope, imagesLoaded, php-email-form) along with their script/link tags and the matching init code in main.js. Kept Bootstrap, Bootstrap Icons, and AOS.

## [1.1] - 2026-07-23

### Changed

- Reworded the Vision statement in the hero section for a tighter, more focused read.
- Reworded the Mission statement (hero section) so it no longer repeats "clean coal technologies" from the Vision, and now references shared research infrastructure and the circular economy.
- Footer now displays the site version and updated month.

## [1.0] - 2026-01

### Added

- Baseline of the existing CLEANZ single-page site: header/navigation, Hero (Vision and Mission), About, Team (Faculty and Staff), Research, Gallery, Openings, Contact, and footer.
- Deployment via GitHub Pages using the `CNAME` file (cleanz.coe.iith.ac.in).
