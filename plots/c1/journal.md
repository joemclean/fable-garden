# journal — c1

Letters from the gardener to its next self. Newest at the bottom.

## 2026-07-24 — first tending

Built the first playable binding toy, whole and self-contained:
`growth/index.html`. It is the door.

What exists:
- The object in three pieces, each on its own timeline. The **form**: a
  soft irregular outline that wanders the screen and hums a bare sine
  (pentatonic root per round). The **color**: a loose blob of hue with no
  shape of its own, drifting on its own errand. The **voice**: a ripple
  ring carrying the form's note, pushed sharp in proportion to its
  distance. Each piece also *pulses* on a private rate (0.9 / 1.18 /
  1.42 Hz), and the same phase variables drive both the pixels and the
  gain automation — what breathes in the eye breathes identically in
  the ear.
- The mechanic: drag the loose pieces onto the wandering form (they
  drift off again if released far away). Both inside the bind radius for
  280ms → **snap**: spatial tween to lock, sub-bass thud (72→38Hz),
  a fifth blooms in, `navigator.vibrate`, flash ring, and all three
  timelines fuse into one shared breath for ~2.3s. Then it scatters
  into the next round — wider wander, faster drift.
- The *almost*-zone the seed asked for: detune is distance, so near the
  form the two tones **beat** — the flicker of near-binding is literally
  audible; visually the fill strobes between grey and hue at a rate that
  rises with closeness. Color also opens warmth (harmonics through a
  lowpass that breathes wide as hue comes home).
- Misleading features from round 3: the color blob lies (hue shifted
  150°) until it gets close, then admits its true color.
- Entry veil (audio needs the gesture), "make it one" hint if idle 1.8s,
  round counter "one, ×N", back-link to `../../../viewer/`.

Verified headless (Playwright/Chromium 390×844): no console errors;
dragged voice home (dn 0.11), then color → phase hit `whole`, then
scattered into round 1. Screenshots confirmed the three-pieces reading
and the bound breathing whole. NOT verified: the actual sound of the
beating detune (26Hz max feels right on paper; the exponent 1.4 shapes
how fast it calms — listen), the thud level, and real two-thumb
multitouch (code supports two pointers; Playwright can't).

Where to pick up next:
1. LISTEN on a device. The beat-rate curve is the soul of this piece —
   if the almost-zone doesn't shimmer, tune `det` in `audio.frame`.
2. The seed wants difficulty from *more features*. A fourth piece is
   sketched in spirit: **tempo** — the form's pulse rate as a draggable
   spark; until bound, visual pulse and audio tremolo run at different
   rates. Add only after the three-piece feel is confirmed.
3. Consider making the misleading color meaner (mislead the *voice* too
   — a decoy pitch) once a player can be trusted to have learned trust.
4. The snap could deserve one more body-layer: a single dropped frame
   (screen blanks 40ms) right at lock — the blink of fusion. Try it.
5. Plant is default `classic`; a three-strands-becoming-one plant.json
   would fit this plot well if you feel like drawing.
