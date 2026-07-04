---
name: frontend-dev
description: "FrontendDev — unique, SEO-complete frontend design and build skill that breaks the generic AI look. Every site gets a one-off Design DNA (named palette, type pair, layout concept, signature element) validated against a banned-pattern catalog of known AI tells, built with full SEO integration (keyword research via Semrush MCP or WebSearch fallback, semantic HTML, schema.org JSON-LD, sitemap, Core Web Vitals budgets), and verified through a screenshot self-critique loop. Analyzes user-supplied reference sites (visual + code token extraction into a Reference Design Brief) and sources real components from 21st.dev / shadcn/ui / Aceternity / Magic UI — always fetched live and re-skinned to the project DNA, never shipped as-is. Stack chosen per project (Next.js/React/Tailwind, plain HTML/CSS/JS, Vue/Nuxt, Astro). Triggers: unique frontend, distinctive design, landing page, marketing site, portfolio, benzersiz site, benzersiz tasarım, AI görünümü olmayan, yapay zeka gibi durmasın, referans site, bu siteye benzet, tasarım çek, 21st.dev, SEO uyumlu frontend, SEO uyumlu site."
metadata:
  version: "1.0.0"
  last_updated: "2026-07-04"
---

# FrontendDev — Unique, SEO-Complete Frontend Design & Build

One mission: ship frontends that (1) could not be mistaken for AI output or a template, (2) are unique per project — the same brief twice must produce two different designs, and (3) rank — SEO is a build input, not an afterthought.

Approach every brief as the design lead of a studio hired specifically because the client rejected templated work. Make deliberate, opinionated, justifiable choices. Deliberateness — a choice actually evaluated against the default — is the entire game.

## Hard Rules (never skip)

1. **No design work before a Design DNA exists.** Phase 3 output is mandatory for every build.
2. **Every DNA is checked against `data/banned-patterns.md`** before code is written. Any hit → regenerate that axis.
3. **SEO research precedes page architecture.** Keywords decide page structure, headings, and URLs — not the other way around.
4. **Fetched component code never ships as-is.** Every token (color/font/spacing/radius/shadow) is remapped to the project DNA; see `references/component-sourcing.md`.
5. **No build is "done" until it passes the screenshot self-critique loop** in `references/anti-generic.md` (desktop + mobile, and dark mode if the DNA includes one).
6. **Reference sites are principle sources, not pixel sources.** Never copy literal copy, imagery, or exact CSS values from a reference (IP + quality risk).
7. **Accessibility beats distinctiveness** whenever they conflict. Quality floor, never announced: responsive to 375px, visible keyboard focus, WCAG AA contrast, `prefers-reduced-motion` respected.

## Workflow — 6 Phases

| Phase | What happens | Load |
|---|---|---|
| 1. Brief intake | Pin down: concrete subject, sector, audience, the page's single job, reference URLs?, stack preference?, existing brand assets? Missing pieces → ask 2-4 batched questions (AskUserQuestion when available; otherwise state assumptions explicitly and proceed). | — |
| 2. Reference analysis *(only if URLs given)* | Visual (screenshot/live inspect) + code (WebFetch HTML/CSS) token extraction → written **Reference Design Brief**. Multiple refs → find the shared thread, don't stitch. | `references/reference-analysis.md` |
| 3. Design DNA | Roll the style matrix: palette (4-6 named hex), font pair, layout skeleton (ASCII wireframe), signature element, motion level, imagery treatment. Check against banned patterns. Same-brief-twice must diverge. | `references/design-dna.md` + `data/style-axes.csv` + `data/font-pairings.csv` + `data/banned-patterns.md` |
| 4. SEO foundation | Keyword research (Semrush MCP → WebSearch fallback) → keyword map → page architecture, URL structure, heading plan, content plan, schema plan, CWV budgets. | `references/seo-full.md` |
| 5. Build | Pick stack via decision tree. Write code from the DNA — every color/type/spacing decision derives from it. Components needed? Fetch live + transform. | `references/stack-selection.md`, `references/component-sourcing.md` + `data/component-sources.csv` |
| 6. Self-critique loop | Screenshot (Claude Preview / Chrome MCP / Playwright) → score against the 10-point AI-tell test → below threshold: revise the failing axis, re-screenshot. Also run the two-bar check: distinctive AND sophisticated. | `references/anti-generic.md` |

Phases 2 and 4 can run in parallel thinking; everything else is sequential. For a redesign of an existing page, phase 1 additionally includes reading the current code and listing what survives.

## Uniqueness Mechanism (why no two outputs match)

- **Entropy sources** in phase 3: brand name letterforms, sector materials/artifacts/vernacular, audience temperament, and an explicit instruction to pick a *different* combination of style axes than the obvious first roll. If your first instinct for the palette/layout is what you'd produce for any similar prompt — that is the definition of generic; discard it and roll again.
- **Banned-pattern catalog** (`data/banned-patterns.md`): the known AI-look clusters, palettes, skeletons, components, copy phrases, and motion clichés. Hard blocklist plus conditional entries.
- **Self-critique loop**: the outside view. Judging distinctiveness from inside the build always flatters; the screenshot test against the checklist (and against 2-3 real competitor sites when possible) is the reliable bar.

## What This Skill Is Not

- Not a maximalism mandate — deliberate restraint is a valid, often superior strategy. Flat emptiness is not restraint; see the two-bar check.
- Not for pure utility UI (admin panels, internal tools) where predictability beats novelty — there, apply only the quality floor and SEO phases that make sense.
- Does not modify or replace the other installed design skills; it is self-contained.
