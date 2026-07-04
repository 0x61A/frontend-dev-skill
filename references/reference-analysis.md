# Reference Site Analysis — Visual + Code

Use when the user points at one or more existing sites ("make it feel like X", "bu siteye benzet", a 21st.dev/Awwwards/Dribbble link). Goal: turn URLs into a written **Reference Design Brief** before any code — not a clone, not a vibe guess.

## Core rule: extract principles, not pixels

Never copy a reference's literal copy, imagery, or exact CSS values (IP risk + produces a worse uncredited clone). Write the brief as *decisions* — palette family, type pairing style, layout pattern, motion restraint level — not lifted values. The measured values below are evidence for identifying the decisions, not material to paste.

## Process

### 1. Code pass — WebFetch every URL
Extract from HTML + linked same-origin CSS:
- **Color:** background/ink/accent hex values and their frequency; CSS custom properties if defined (a `--brand-*` block is the site telling you its palette).
- **Type:** `font-family` stacks per role (display vs body vs mono), weight range in use, approximate scale ratio.
- **Space & geometry:** spacing rhythm (consistent scale? multiples of what?), border-radius values, border/shadow strategy.
- **Structure:** section order, landmark usage, heading hierarchy, grid patterns (`grid-template-columns`, flex direction changes), CTA placement strategy, copy tone.
This is text-level: it tells you *what* the page does, not how it lands visually.

### 2. Visual pass — live browser when available
Priority order of tools in this environment:
1. **Chrome MCP** (`claude-in-chrome`): open the URL, screenshot, `read_page` for structure. Best for real rendering incl. JS-built pages.
2. **Claude Preview** pointed at the URL (when the reference runs locally) — `preview_inspect` gives *computed* styles, strictly more reliable than declared CSS.
3. **Playwright via Bash** (`npx playwright screenshot <url> out.png`) as fallback.
Observe what code can't show: visual hierarchy (where does the eye land first/second/third), scale contrast, density, image treatment, motion (what animates, how fast, what easing feeling), scroll behavior. Screenshot mobile width too — a reference that collapses badly is a warning, not a model.

No browser available → say so explicitly, proceed on the code pass alone, and mark visual conclusions as inferred.

### 3. Multiple references → shared thread
Don't average or stitch. Find the throughline ("all three: high-contrast photography, minimal chrome, mono labels") and build the brief on that. Per-site one-offs get noted and left out. Mismatched references (a brutalist zine + a luxury spa) → tell the user they conflict and ask which axis wins.

### 4. Emit the Reference Design Brief

```
Reference(s): <url(s)>
Shared thread: <one sentence — the thing actually being borrowed>
Palette direction: <family + role, e.g. "warm neutral base, single saturated accent for CTAs">
Typography direction: <pairing style + contrast strategy, not font names to copy>
Layout pattern: <named pattern, e.g. "asymmetric hero, off-grid image, sticky sidebar nav">
Density & geometry: <airy/dense, radius/border character>
Motion level: <restrained | moderate | expressive + what was specifically observed>
Imagery treatment: <what makes their images consistent>
Why it works: <1-2 sentences — the causal read, this is the real deliverable>
Deliberate divergence: <what we change on purpose and why — mandatory, non-empty>
```

**"Deliberate divergence" is mandatory.** A brief without it produces a clone. The divergence typically becomes the DNA's signature element or a different layout skeleton pick.

### 5. Confirm before building
The brief is cheap to correct; a page built on a misread reference is not. Interactive session → show it, get a nod. Autonomous run → state it and proceed.

## Failure modes checklist

- Copying instead of extracting (exact hexes/fonts lifted verbatim into the DNA).
- Eyeballing colors from a screenshot instead of reading them from CSS/computed styles.
- Stitching mismatched references instead of naming the conflict.
- Skipping the mobile view of the reference.
- Inheriting the reference's accessibility problems (their contrast failure is not a design direction).
- Treating a reference behind heavy JS as "minimal" because WebFetch saw an empty shell — check with a live browser before concluding.
