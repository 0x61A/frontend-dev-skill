# Anti-Generic — the Self-Critique Loop

Judging distinctiveness from inside the build always flatters: every individual choice already feels considered. The loop below is the outside view. **No build is done until it passes.**

## The loop

1. **Render + screenshot.** Priority: Claude Preview (`preview_start` → `preview_screenshot`, plus `preview_inspect` for exact colors/fonts — screenshots lie about precise values); else Chrome MCP on the local URL; else `npx playwright screenshot`. Capture: desktop (1280+), mobile (375), and dark mode if the DNA includes one.
2. **Score the 10-point AI-tell test** (below). Each item pass/fail, honestly.
3. **8/10 or any HARD banned-pattern visible → fail.** Identify the failing *axis* (palette? skeleton? type? copy?), revise that axis against the DNA card — don't randomly restyle. Re-screenshot. Repeat until pass. Two consecutive failed loops on the same item → the DNA itself is generic on that axis; go back to phase 3 and reroll it.
4. **Competitor lineup when possible:** screenshot 2-3 real competitor/same-sector sites and view side by side. Indistinguishable in the lineup — same layout shape, same color temperature, same type feel — means revisit one major decision. This is the single most reliable distinctiveness instrument.

## The 10-point AI-tell test

1. **Skeleton:** Is this the universal template flow (kicker → centered headline → subhead → 2 buttons → 3-up cards → CTA band)? Does at least one section break centered-stack flow?
2. **Palette:** Would this exact palette appear for a different sector's brief unchanged? Do the colors trace to the subject's world?
3. **Type:** Is the display face a default (Inter/Roboto/system)? Does the type treatment itself carry personality — deliberate breaks, scale, weight contrast?
4. **Signature:** Can you point at THE one memorable element? Is it derived from the subject, or bolt-on decoration?
5. **Copy:** Any BP21/BP23 phrase? Does the copy name concrete things from the subject's world?
6. **Cards & icons:** Emoji icons? The identical icon-title-two-gray-lines card ×3? Uniform border-radius everywhere without a stated geometry strategy?
7. **Imagery:** Generic stock / untreated AI images? Or a consistent, named treatment?
8. **Motion:** Fade-in-up on everything? Or one signature curve used deliberately (or deliberate stillness)?
9. **Density & depth:** Real layering, texture, considered density — or flat rectangles and vast gaps that read "afraid to commit"?
10. **The cold look:** Squint at the screenshot as a stranger. First 2 seconds: template, or someone's actual work?

## The two-bar check — distinctive ≠ sophisticated

Clearing "not templated" does nothing for "actually looks good". The most common escape from the generic skeleton — strip to flat blocks, huge empty space, minimal-everything — lands somewhere cheap, sparse, unfinished. Field-tested failure: a bookstore page of flat colored rectangles standing in for covers was un-templated and read like a bar chart next to the warm, layered, photographic sites it was meant to rival. The fix was craft and richness — atmospheric imagery, layered depth (overlaps, insets, badges), textured detail, considered density — not more distinctiveness.

Check both, separately:
- **Distinctive?** → 10-point test + competitor lineup.
- **Sophisticated?** → Does it look like a studio made it, or a first draft afraid to commit? Real depth (imagery, layering, texture, shadow, considered type scale) or just flat shapes and gaps? Would a paying client see richness or "unfinished"? Restraint is deliberate and rich; flatness is absence.

## Multi-page / multi-session rule

Sites built in one session drift into siblings: five sectors, five palettes, one identical skeleton — different skin, same skeleton, invisible from inside. Run the lineup check across your *own set* too: screenshot every page/site produced in the session side by side; near-identical section maps → vary the layout skeleton axis, not just the paint.

## Quality floor (enforced silently, never announced as a feature)

- Responsive to 375px without horizontal scroll or broken composition.
- Visible keyboard focus states (`:focus-visible`), logical tab order; horizontal-scroll sections keyboard-operable.
- WCAG AA contrast on body text (4.5:1) and UI text (3:1) — verify with computed values via `preview_inspect`, not by eye.
- `prefers-reduced-motion` honored: signature motion collapses to a static equivalent.
- Custom form controls remain labelled, focusable, screen-reader-sane.
- Accessibility beats distinctiveness on every conflict, no exceptions.
