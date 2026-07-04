# Full SEO Integration

SEO is a **build input**: keyword research runs before page architecture, and page architecture decides what gets designed. A beautiful page built on the wrong keyword map is rework.

## Phase order

### 1. Keyword research

**Semrush MCP connected** (tools like `keyword_research`, `organic_research`, `overview_research`): use real data — do not answer from general knowledge when data can be retrieved.
- `keyword_research` on 3-5 seed terms from the brief → volume, difficulty, intent. Default `database` to the target market (`tr` for Turkish projects, `us` default).
- `organic_research` on 2-3 competitors (user-named, or found via one WebSearch) → what they rank for, gaps.
- Output: primary keyword per page + 3-6 secondary/long-tail per page, mapped to intent (informational/commercial/transactional).

**No Semrush** → WebSearch fallback: search the seed terms, read the SERP — what page *types* rank (product pages? guides? comparisons?), what the `People also ask` questions are, how titles are phrased. Coarser, but page-type intent evidence is the most decision-relevant signal anyway. Say explicitly that volumes are unknown.

**Neither available** (offline): state the assumption set and derive keywords from the subject + audience logically; flag for later validation.

### 2. Keyword map → architecture
- One primary keyword ↔ one page. Two pages targeting the same primary keyword = cannibalization; merge or differentiate.
- URL structure from the map: short, hyphenated, keyword-bearing, no dates/IDs (`/kahve-kavurma-atolyesi` not `/page?id=7`).
- Heading plan per page: single `h1` carrying the primary keyword naturally; `h2`s cover the subtopics/questions the research surfaced; hierarchy never skips levels.
- Internal link plan: which page links to which, with descriptive (not "click here") anchors.
- Content plan: per page, what questions it must answer to satisfy the ranking intent — this feeds the copywriting in the build phase.

### 3. On-page mandatories (every page, non-negotiable)
- Unique `<title>` ≤ 60 chars, primary keyword near the front; meta description ≤ 155 chars written as a SERP click-through pitch.
- Canonical URL; Open Graph + Twitter card (og:title, og:description, og:image 1200×630, og:type, twitter:card).
- Semantic landmarks: `header/nav/main/section/article/aside/footer` — a `div`-only page is a rejected page.
- Every meaningful image: descriptive `alt` (what it shows, in context — not keyword stuffing), explicit `width`/`height` (CLS), lazy-loading below the fold, modern format (AVIF/WebP with fallback).
- `lang` attribute correct (`tr`, `en`…); multilingual → `hreflang` pairs.
- Descriptive internal anchor text; no orphan pages.

### 4. Structured data — accuracy over coverage
JSON-LD in `<head>`, matching what's visibly on the page (invisible schema is a manual-action risk). Per page type:
- Any site: `Organization` (or `Person` for portfolios) + `WebSite`.
- Local business: `LocalBusiness` subtype with real NAP, `openingHours`, `geo`.
- Products: `Product` + `Offer` (price/currency/availability); reviews only if real.
- Articles/blog: `Article`/`BlogPosting` with author, dates.
- FAQ sections: `FAQPage` matching the visible questions. Breadcrumbs: `BreadcrumbList`.
Validate mentally against schema.org requirements; when Chrome MCP is available, validator.schema.org can be used for a live check.

### 5. Site plumbing
- `sitemap.xml`: canonical URLs only (200, indexable, non-duplicate), `lastmod` real. Generated at build time in frameworks (Next: `app/sitemap.ts`; Astro: `@astrojs/sitemap`), static file for plain HTML.
- `robots.txt`: allow crawl, point to sitemap. Block only genuinely private paths — never block CSS/JS.
- 404 page real (returns 404, not soft-200 redirect).
- Optional, offer for content-rich sites: `llms.txt` for AI-crawler orientation (GEO — AI Overviews/ChatGPT/Perplexity increasingly source cited answers).

### 6. Core Web Vitals budgets — design-time, not audit-time
Targets: **LCP < 2.5s · CLS < 0.1 · INP < 200ms.** Enforced during design, not patched after:
- Fonts: max 2 families + 1 optional utility, subset weights actually used, `font-display: swap`, preload the display face's woff2, `size-adjust`ed fallback metrics to kill swap-shift. (Fontshare/self-hosted faces: same rules, self-host the files.)
- LCP element (hero image/headline): no lazy-load on it, `fetchpriority="high"` on a hero image, responsive `srcset`+`sizes`.
- CLS: dimensions on all media/embeds; no layout-shifting entrance animations on above-fold content (animate `transform`/`opacity` only).
- INP: signature interactive elements (canvas, cursor effects) must not block the main thread — `requestAnimationFrame`, passive listeners, idle-until-needed. The DNA's motion budget is also a performance budget.
- JS discipline: SEO-critical content must exist in server-rendered/static HTML, never client-render-only (see stack-selection.md).

## Verification pass (after build)
1. View source: title/meta/canonical/OG/JSON-LD present in initial HTML (not injected post-load).
2. Heading tree correct (one h1, no skipped level) — quick check: `grep -o '<h[1-6]' page | sort | uniq -c`.
3. All images have alt + dimensions.
4. sitemap.xml + robots.txt resolve.
5. Lighthouse when runnable (`npx lighthouse <url> --only-categories=seo,performance`) — treat scores as a floor, not the goal.
