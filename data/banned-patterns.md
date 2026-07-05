# Banned Pattern Catalog — the AI-Look Blocklist

Two tiers. **HARD** entries are banned unless the user explicitly asks for them by name (the brief's own words always win). **CONDITIONAL** entries are banned as defaults but allowed when a stated, brief-specific justification exists — write the justification down in the DNA card.

## HARD — Palettes & Color

- BP01. Cream `#F4F1EA`-family background + high-contrast serif display + terracotta accent (AI-look cluster #1).
- BP02. Near-black background + one acid-green or vermilion accent, nothing else (AI-look cluster #2).
- BP03. Purple-to-blue (or indigo-violet) gradient hero background. Includes `#667eea → #764ba2` and neighbors.
- BP04. Gradient-mesh / aurora blob backgrounds as the primary hero visual.
- BP05. The framework-default palette left untouched (Tailwind `blue-500`/`indigo-600` as brand color, default shadcn zinc theme).
- BP06. Same accent color the sector's top 5 sites already use, chosen without noticing (SaaS = electric blue, eco = leaf green, fintech = navy).

## HARD — Typography

- BP07. Inter, Roboto, Open Sans, or system-ui as the *display* face. (As a body/utility face: conditional — must be a stated choice, and never paired with a default look elsewhere.)
- BP08. One font family doing every job with no weight/width contrast strategy.
- BP09. Headline autowrapping wherever the container breaks it, on a hero. Hero display type gets deliberate line breaks.

## HARD — Layout & Structure

- BP10. The universal skeleton: kicker → centered headline → subhead → two buttons → 3-up icon-card feature grid → logo strip → testimonial carousel → CTA band → footer. Different skin, same skeleton is still this pattern — at least one section must break the centered-stack vertical flow.
- BP11. Broadsheet layout: hairline rules everywhere, zero border-radius, dense newspaper columns (AI-look cluster #3) — unless the subject genuinely is editorial/news.
- BP12. Every section = full-width centered column with uniform viewport-height blocks and identical padding.
- BP13. Numbered 01/02/03 markers on content that has no real sequence.
- BP14. Glassmorphism card stacks as the default surface treatment.
- BP15. Bento grid used because it's trendy, with cell contents that don't justify differing cell sizes.

## HARD — Components & Imagery

- BP16. Emoji as feature icons (🚀✨💡) or emoji anywhere in UI chrome.
- BP17. Identical 3-column card: icon top-left, bold title, two lines of gray text — repeated as the only content pattern.
- BP18. Generic stock photography (handshakes, laptop-with-coffee, diverse-team-laughing) or default-style AI-generated images with no consistent treatment.
- BP19. Unstyled default browser form controls on a brand-forward page.
- BP20. Floating phone/laptop mockup at a 15° angle with a soft shadow as the hero image, when the product isn't even an app.

## HARD — Copy

- BP21. Template marketing phrases: "Elevate your…", "Unlock the power of…", "Seamlessly…", "Empower your…", "Take your X to the next level", "Supercharge…", "Revolutionize…", "…made simple/easy", "All-in-one platform for…".
- BP22. Feature-benefit triads that could describe any product in the category ("Fast. Secure. Reliable.").
- BP23. Turkish equivalents: "…'i bir üst seviyeye taşıyın", "…'in gücünü keşfedin", "Hepsi bir arada", "Kusursuz deneyim", "Dijital dünyada yerinizi alın", "Fark yaratın", "Hayallerinizdeki…". (Good replacements: `data/microcopy-tr.md`.)

## HARD — Motion

- BP24. Fade-in-up on scroll applied to every element uniformly.
- BP25. Mixed animation vocabularies — components from different libraries with different easings/durations on one page.
- BP26. Infinite marquee logo strip as the only motion on the page.

## HARD — Composition Repeats (self-inflicted AI look)

Field-tested failure: two same-session builds with different palettes, fonts and skeletons still read as siblings because both used a diagonal clip-path hero with one large circular object. Distinctiveness lives at the composition level too.

- BP32. Diagonal/angled clip-path hero with a single large circular/disc object as the visual anchor — this exact cluster has already repeated in practice. Pick a different `hero_composition` axis option.
- BP33. Emitting a DNA that matches any `design-log.md` row on **2 or more** of: `layout_skeleton`, `hero_composition`, palette family. Reroll the overlapping axes before emitting (see design-dna.md step 6).
- BP34. Purple/indigo glow-orb, neon-gradient beam, or "AI aesthetic" luminous backdrop as the hero atmosphere.
- BP35. Uniform card grid where every card does the identical tilt/lift/glow on hover as the page's only interaction idea.

## CONDITIONAL — allowed with written justification in the DNA card

- BP27. Dark theme with single bright accent — allowed for genuinely technical/developer subjects, but must diverge from Linear/Vercel in layout skeleton and type.
- BP28. Centered hero — allowed when the signature element itself lives in the hero and carries the distinctiveness.
- BP29. Serif display + warm neutral base — allowed for editorial/craft/heritage subjects with a palette measurably distinct from BP01 (no `#F4F1E*` family, no terracotta default accent).
- BP30. Border-radius = 0 everywhere — allowed for brutalist/industrial directions actually rooted in the subject.
- BP31. Testimonial/logo sections — allowed with real (user-provided) names and marks; never fabricate logos or personas.
- BP36. Spline/3D-blob or floating abstract 3D shapes as the hero visual — allowed only when the product itself is 3D/spatial (3D tools, games, hardware with real renders).

## Pass Criteria (checked in phase 3 and again in phase 6)

1. Zero HARD hits; every CONDITIONAL used has a one-line written justification.
2. The page carries **at least one signature element derived from the subject's real world** (its materials, instruments, artifacts, vernacular).
3. Palette and type pairing each have a one-line sector-specific rationale that would not transfer to a different sector unchanged.
4. At least one section breaks the centered-stack flow (asymmetry, bleed, scale contrast, color-block zoning, or broken grid).
5. Copy names concrete things from the subject's world; no BP21/BP23 phrase survives.
6. The DNA has been checked against `design-log.md` — no 2+ axis overlap with any prior build (BP33), and the log gains a row when phase 6 passes.
