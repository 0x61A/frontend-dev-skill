# Stack Selection — Per Project, Not One Default

User's stated preference always wins. Existing codebase always wins (match what's there). Otherwise, decide from the decision tree and **state the choice + reason in one line** before building.

## Hard constraint from SEO
SEO-critical content must be in the initial HTML response. **CSR-only React/Vue (Vite SPA, CRA) is disqualified for any page that needs to rank.** SPA acceptable only for behind-login app surfaces.

## Decision tree

1. **Static content site, landing page, portfolio, brochure, small business** (no server logic, few pages)
   → **Plain HTML/CSS/JS** (hand-rolled or Vite multi-page). Zero framework tax, best CWV by default, deploys anywhere.
   → If page count grows or content is collection-shaped (blog, menu, catalog) → **Astro** (islands, content collections, `@astrojs/sitemap`, ships ~zero JS by default).

2. **Marketing site + blog + some interactivity, or SaaS front + app together**
   → **Next.js (App Router) + Tailwind**. SSG/ISR for marketing pages, server components by default, `app/sitemap.ts` + Metadata API cover SEO plumbing. The shadcn ecosystem (component-sourcing.md) is native here.

3. **Team/codebase is Vue**
   → **Nuxt** (SSR/SSG via nitro presets, `useSeoMeta`, `@nuxtjs/sitemap`). Component sources: Flowbite Vue, daisyUI (CS12/CS13).

4. **Content-heavy publishing at scale** (100s of pages, editorial)
   → **Astro** first; Next.js if the team already lives in React or needs heavy app features.

5. **E-commerce**
   → Existing platform (Shopify etc.) → build within it (headless only when the DNA demands frontend freedom the theme can't give). Greenfield → Next.js + platform APIs.

6. **Dashboard/app behind login** (SEO irrelevant)
   → Whatever fits the team; SPA fine. Only the quality floor applies, not the distinctiveness machinery (SKILL.md "What This Skill Is Not").

## Styling layer
- Tailwind when using Next/Nuxt/Astro with component sourcing (the ecosystem assumes it). DNA tokens live in the Tailwind theme config — never inline arbitrary values when a token exists.
- Plain HTML builds: vanilla CSS with custom properties as the token layer (`:root { --ink: …; --paper: …; }`). Watch selector specificity — type-level and class-level rules cancelling each other's spacing is a classic self-inflicted bug.
- CSS-in-JS: only if the existing codebase already uses it.

## Fonts by stack
- Next.js: `next/font` (self-hosts Google fonts, zero layout shift). Fontshare faces: download + `next/font/local`.
- Astro/plain: self-host woff2 + preload; avoid the double-request of CSS @import chains.

## Deploy note (only when asked to deploy)
Static/Astro → Netlify/Cloudflare Pages/Vercel all fine. Next.js with ISR/server components → Vercel is the least-friction path. Don't deploy unprompted.
