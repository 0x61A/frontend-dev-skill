# Multi-Page Sites — One DNA, Sibling Pages

Use when the build has more than one page (site + blog, service pages, catalog…). The failure modes are opposite twins: pages that look like different websites (broken DNA), or pages that are the same template stamped N times (clones). Target: **siblings, not clones** — same family resemblance, different posture.

## One token source

- The DNA lives in exactly one place: `:root` custom properties in a shared CSS file, or the Tailwind theme config. Page-local color/font/spacing literals are bugs — every page imports the same tokens.
- Shared chrome (nav, footer, skip-link) is byte-identical across pages: one include/component/layout, never copy-pasted per page (copies drift).
- The signature element appears on every page, but scaled to the page's job — full-size on the home hero, echoed as a motif elsewhere (the coffee-ring that anchors the home page becomes a section divider on the menu page).

## Skeleton variation rule

- The home page's `layout_skeleton` + `hero_composition` picks belong to the home page. Interior pages stay in the same *family* but vary **density and hero scale**: an interior page gets a compressed masthead (one-third viewport or less), not a re-run of the home hero.
- Two pages with the same section map in the same order = clone smell. Vary at least the opening composition and one structural section per page.
- Utility pages (contact, legal, 404) get the quality floor and the token system, not the full distinctiveness machinery — a distinctive 404 is a nice touch, a "distinctive" privacy policy is noise.

## Navigation + information architecture

- Nav reflects the keyword map from phase 4 (seo-full.md): primary pages in the nav, one descriptive label each — no "Solutions" mystery-meat.
- Breadcrumbs on anything deeper than one level, marked up as `BreadcrumbList` (seo-full.md §4).
- Internal links: every page reachable within 2 clicks from home; descriptive anchors; the phase-4 internal-link plan is implemented, not decorative.
- Active-page state visible in the nav (aria-current="page" + a visual treatment from the DNA).

## Per-page SEO

Each page keeps its own primary keyword, unique `<title>`/meta description, canonical, and page-appropriate schema type (seo-full.md). The sitemap covers all pages; `lastmod` real per page.

## Verification

Phase 6 runs per page (overflow check + screenshot at minimum for every page; the full 10-point test on the home page and one representative interior page). Then the lineup check across the site's own pages: screenshot all side by side — same skin? good. Same skeleton map? vary it.
