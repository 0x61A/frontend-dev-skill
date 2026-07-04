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
From `data/style-axes.csv`, pick one option per axis: `value_scheme`, `temperature`, `saturation`, `geometry`, `texture`, `density`, `layout_skeleton`, `type_voice`, `motion`, `signature`, `imagery`. Respect each row's `avoid_when`. Justify each pick in ≤1 line against the subject — a pick you can't justify is a default wearing a costume.

**Mandatory:** the `layout_skeleton` pick must be deliberate, not "centered stack because it's safe". A sector-appropriate palette on the universal skeleton is still the universal skeleton (banned BP10/BP12).

### 2. Derive the palette — 4-6 named hex values
Derive from the subject's real world, not from a color-theory chart: the actual color of roasted beans, courtroom oak, stage lighting. Name each value by what it *is* ("roast-brown #3E2B23", "parchment #F2EBDC" — names are part of the DNA). Check: base/ink contrast ≥ WCAG AA for body text; accent works on both base and ink. Then check against `data/banned-patterns.md` BP01-BP06.

### 3. Pick the type pair
From `data/font-pairings.csv` — or a justified custom pair (same quality bar: characterful display used with restraint, complementary body, optional utility face for captions/data). Respect `avoid_when`. Turkish-language projects: verify the display face covers ğ ş ı İ ç ö ü before committing (FP46 is the guaranteed fallback). Set a type scale with intentional weights/widths — the type treatment should be memorable, not a neutral delivery vehicle.

### 4. Layout concept — ASCII wireframes
Sketch 2-3 candidate section maps as ASCII wireframes, one sentence each. Pick one; note why the others lost. The wireframe must show where the skeleton *breaks* the centered-stack flow (asymmetry, bleed, scale contrast, zoning, overlap).

### 5. Signature element — exactly one
The single thing this page will be remembered by, derived from the subject's world (AX43-AX50 lists the types). Spend your boldness here; keep everything around it quiet and disciplined. One signature executed well beats three competing gimmicks. Chanel rule: before shipping, remove one accessory.

### 6. Banned-pattern check
Run the full DNA against `data/banned-patterns.md`. Any HARD hit → regenerate that axis (not the whole DNA). CONDITIONAL use → write the one-line justification into the card. Then run the pass criteria at the bottom of that file.

### 7. Emit the DNA card

```
## Design DNA — <project>
Subject: <one line> · Audience: <one line> · Page job: <one line>
Palette: <name #hex> · <name #hex> · <name #hex> · <name #hex> [· accent(s)]
Type: <display> / <body> [/ <utility>] — <one-line rationale>
Scale/geometry: <radius, border, shadow strategy>
Layout skeleton: <axis pick> — <one-line rationale> + wireframe
Signature: <the one element> — <why it belongs to this subject>
Motion: <level + the one signature easing curve, e.g. cubic-bezier(...)>
Imagery: <treatment>
Conditional justifications: <BPxx: reason — or "none">
Divergence note: <how this differs from the generic version of this brief>
```

The card goes in the conversation (and in the repo as `design-dna.md` for multi-session projects). During build, **derive every value from the card** — a color or font that isn't in the card is a bug.

## Copy Rules (copy is design material)

- Write from the user's side of the screen: name things by what people control and recognize, not how the system is built.
- Concrete beats clever. Real nouns from the subject's world beat category adjectives.
- No phrase from BP21/BP23. If the brief has no real content, invent *specific* content (real-sounding menu items, actual feature behaviors) — never lorem-flavored marketing filler.
- Headlines get deliberate line breaks as part of the composition (BP09).
