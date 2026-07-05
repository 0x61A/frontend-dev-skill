# Design DNA Generation

The DNA is a compact, written token system generated **before any code**: palette, type pair, layout skeleton, signature element, motion level, imagery treatment. Every downstream color/type/spacing decision derives from it. No DNA → no build.

## Inputs

1. **Subject grounding.** If the brief doesn't pin down the product/subject, pin it yourself: name one concrete subject, its audience, and the page's single job — state your choice. The subject's own world (materials, instruments, artifacts, vernacular) is where distinctive choices come from.
2. **Reference Design Brief** (if phase 2 ran) — its "deliberate divergence" line constrains the DNA.
3. **Entropy sources** — use these to force variation between projects and between runs of the same brief:
   - Brand name letterforms (a name with a double letter, a diacritic, an unusual initial suggests typographic play).
   - Sector materials/artifacts: coffee → kraft paper, roast curves, cupping notes; law → case citations, ledger rules; music → waveforms, sleeve art.
   - Audience temperament: who reads this page and in what mood.
   - **The anti-first-instinct rule:** work through what you would produce for a *generic* version of this prompt. If your current plan matches it, that is the definition of templated — discard the matching axis and roll a different option from `data/style-axes.csv`.

## Process

### 1. Roll the style matrix
From `data/style-axes.csv`, pick one option per axis: `value_scheme`, `temperature`, `saturation`, `geometry`, `texture`, `density`, `layout_skeleton`, `hero_composition`, `type_voice`, `motion`, `signature`, `imagery`. Respect each row's `avoid_when`. Justify each pick in ≤1 line against the subject — a pick you can't justify is a default wearing a costume.

**Mandatory:** the `layout_skeleton` pick must be deliberate, not "centered stack because it's safe". A sector-appropriate palette on the universal skeleton is still the universal skeleton (banned BP10/BP12).

**`hero_composition` is its own axis, not a byproduct of the skeleton.** Field-tested failure: two builds with different skeletons, palettes and type still read as siblings because both landed on the same hero shape (diagonal clip + one big circular object — now BP32). The first 2 seconds of a page are the hero composition; it must be rolled and justified explicitly.

### 2. Derive the palette — 4-6 named hex values
Derive from the subject's real world, not from a color-theory chart: the actual color of roasted beans, courtroom oak, stage lighting. Name each value by what it *is* ("roast-brown #3E2B23", "parchment #F2EBDC" — names are part of the DNA). Check: base/ink contrast ≥ WCAG AA for body text; accent works on both base and ink. Then check against `data/banned-patterns.md` BP01-BP06.

### 3. Pick the type pair
From `data/font-pairings.csv` — or a justified custom pair (same quality bar: characterful display used with restraint, complementary body, optional utility face for captions/data). Respect `avoid_when`. Turkish-language projects: verify the display face covers ğ ş ı İ ç ö ü before committing (FP46 is the guaranteed fallback). Set a type scale with intentional weights/widths — the type treatment should be memorable, not a neutral delivery vehicle.

### 4. Layout concept — ASCII wireframes
Sketch 2-3 candidate section maps as ASCII wireframes, one sentence each. Pick one; note why the others lost. The wireframe must show where the skeleton *breaks* the centered-stack flow (asymmetry, bleed, scale contrast, zoning, overlap).

### 5. Signature element — exactly one
The single thing this page will be remembered by, derived from the subject's world (AX43-AX50 lists the types). Spend your boldness here; keep everything around it quiet and disciplined. One signature executed well beats three competing gimmicks. Chanel rule: before shipping, remove one accessory.

### 6. Banned-pattern + design-log check
Run the full DNA against `data/banned-patterns.md`. Any HARD hit → regenerate that axis (not the whole DNA). CONDITIONAL use → write the one-line justification into the card. Then run the pass criteria at the bottom of that file.

**Design-log check (BP33):** read `design-log.md` at the skill root. If the new DNA matches any row on **2 or more** of `layout_skeleton`, `hero_composition`, palette family → reroll the overlapping axes. One shared axis across builds is fine; two is a fingerprint. The log is append-only and persists across sessions — this is what makes "same brief twice diverges" true beyond a single conversation. (The row is appended after the phase-6 pass; see anti-generic.md.)

### 7. Emit the DNA card

```
## Design DNA — <project>
Subject: <one line> · Audience: <one line> · Page job: <one line>
Palette: <name #hex> · <name #hex> · <name #hex> · <name #hex> [· accent(s)]
Type: <display> / <body> [/ <utility>] — <one-line rationale>
Scale/geometry: <radius, border, shadow strategy>
Layout skeleton: <axis pick> — <one-line rationale> + wireframe
Hero composition: <axis pick> — <one-line rationale>
Dark mode: <none | derived — see Dark Mode section>
Design-log check: <clean | rerolled <axis> (overlapped with <project>)>
Signature: <the one element> — <why it belongs to this subject>
Motion: <level + the one signature easing curve, e.g. cubic-bezier(...)>
Imagery: <treatment>
Conditional justifications: <BPxx: reason — or "none">
Divergence note: <how this differs from the generic version of this brief>
```

The card goes in the conversation (and in the repo as `design-dna.md` for multi-session projects). During build, **derive every value from the card** — a color or font that isn't in the card is a bug.

## Dark Mode (only when the DNA includes one)

- Derive the dark palette from the same real-world anchors as the light one — **never invert**. The roast-brown that anchored light mode has a dark-room counterpart (the unlit drum, the ember); name those hexes the same way.
- Decide delivery: `prefers-color-scheme` only (marketing pages) vs. manual toggle + stored preference (apps, reading-heavy sites). State the choice in the card.
- Contrast is re-verified in dark independently — WCAG AA numbers that passed on light do not transfer. Accent colors usually need a lightness bump.
- Phase 6 already requires a dark screenshot when the DNA includes one; the dark variant runs the same 10-point test.

## Copy Rules (copy is design material)

- Write from the user's side of the screen: name things by what people control and recognize, not how the system is built.
- Concrete beats clever. Real nouns from the subject's world beat category adjectives.
- No phrase from BP21/BP23. If the brief has no real content, invent *specific* content (real-sounding menu items, actual feature behaviors) — never lorem-flavored marketing filler.
- Headlines get deliberate line breaks as part of the composition (BP09).
- Turkish projects: pull CTA verbs, form labels, and tone patterns from `data/microcopy-tr.md` — subject-specific verbs ("Yerimi ayırt", "Eskiz talep et") beat generic ones ("Gönder", "Başla").
