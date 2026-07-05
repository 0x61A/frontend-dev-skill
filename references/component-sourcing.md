# Component Sourcing — Fetch + Transform

Use when a ready-made component/section accelerates the build ("grab a pricing table", "21st.dev'den çek"). This is *actual reusable code* from a marketplace — different from reference analysis (visual inspiration, code never copied). The deal here: **code may be copied in, but it never ships in its source form.**

## Process

### 1. Identify the need precisely
Component type (hero, navbar, pricing, dashboard shell…), framework constraint (React/Vue/plain HTML), Tailwind or not, budget (free-only?), and whether in-repo ownership (shadcn model) matters.

### 2. Pick a source
`data/component-sources.csv` (16 sources with tradeoffs). Quick guide:
- shadcn ecosystem, big selection → **21st.dev** (CS01); primitives → **shadcn/ui** (CS02); official full pages → **Blocks** (CS03)
- Animated marketing wow → **Aceternity** (CS04) or **Magic UI** (CS05) — never both on one page
- Zero budget, no React → **Hyperui** (CS09), **Preline** (CS10)
- Non-React frameworks → **Flowbite** (CS13), **daisyUI** (CS12)
- Dashboards/charts → **Tremor** (CS15)
For brand-forward pages, surface 2-3 candidates with tradeoffs when the session is interactive; pick and state reasoning when autonomous.

### 3. Fetch live — never from memory
WebFetch (or Chrome MCP) the specific component's page for the **current** markup/JSX/install command. These libraries change APIs and file structures; a from-memory reconstruction is a bug waiting to happen. Note the license/tier while you're there (paid marketplaces: verify seat/usage terms before client work).

### 4. Transform — the mandatory re-skin
The fetched code enters as raw material. Before it's committed:

| What | Rule |
|---|---|
| Colors | Every literal color and palette class (`bg-zinc-900`, `text-indigo-500`, hex values) → the project's DNA tokens. Zero source-palette survivors. |
| Typography | Font families, sizes, weights → DNA type scale. Component-local font imports deleted. |
| Geometry | radius/border/shadow values → DNA geometry strategy. A pill-shaped component in a sharp-geometry DNA gets re-cut, not tolerated. |
| Spacing | Internal padding/gaps remapped onto the project's spacing scale. |
| Motion | Easings/durations retimed to the DNA's signature curve. If the DNA motion level is *restrained* and the component is animation-heavy, strip the animation — don't keep it because it looked cool in the preview. |
| Structure | Class names/CSS vars renamed to project conventions; dead variants, demo copy, placeholder images, and author branding removed. |
| Content | Demo copy replaced with real subject-derived copy (see design-dna.md copy rules). |

**The two-token-systems rule:** a codebase must have exactly one color/spacing/type system after integration. Two competing systems (project tokens + the component's leftovers) is the most common integration failure — grep for the source library's characteristic classes/vars after integrating to prove they're gone.

### 5. Audit what came in
- **A11y:** imported components routinely miss labels, focus order, aria states — check before trusting, especially community sources (21st.dev is user-published).
- **Deps:** each new package justified; watch for a component quietly pulling a large animation library the project didn't need. Any unexpected network call or inline script → remove.
- **CWV:** animation-first components carry INP/CLS cost — test after integration, not just before.

### 6. Distinctiveness re-check
A popular library's default look is by definition something many other sites already ship. After transform, the component should read as *this project's* — if a section still visually announces its source library, the transform isn't done. Final arbiter: the phase-6 self-critique loop.

## AI generators (v0.dev, 21st.dev AI mode)
Same pipeline, stricter: output is a first draft, not a deliverable. Full review + transform + a11y pass, and expect redundant state and missing aria attributes in generated code.

## Imagery sourcing

Same fetch-and-transform philosophy as components: an image may come from outside, but it never ships untreated.

**Sources + license notes:**
- **Unsplash** (unsplash.com) — free, no attribution required (appreciated); Unsplash License forbids reselling unmodified copies and compiling into a competing service.
- **Pexels** (pexels.com) — free photos + video, no attribution required; identifiable-people-in-endorsement caveat applies.
- **Openverse** (openverse.org) — CC-licensed aggregate; **check the per-image license** (some are CC BY / BY-SA → attribution or share-alike obligations).
- Client work: confirm the license permits commercial use before shipping; log the source URL per image.

**Mandatory treatment:** every image passes through the DNA's imagery treatment before it ships — raw stock is BP18. Concrete CSS recipes:
- Duotone: `filter: grayscale(1) contrast(1.1)` + a `mix-blend-mode: multiply`/`screen` color overlay from the palette.
- Grain: SVG `feTurbulence` overlay at low opacity (see any AX17 build).
- Irregular masks: `clip-path` polygons or `mask-image` gradients derived from the DNA geometry.
- Consistent grade: one shared `filter` custom property applied site-wide, never per-image tweaks.

**AI-generated imagery:** allowed only as a last resort, always disclosed to the user, and only with the same consistent treatment applied — a raw AI render dropped into a page is the strongest AI-tell there is (BP18). Never fake photographic "proof" (team photos, premises, products that don't exist).
