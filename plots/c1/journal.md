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

## 2026-07-25 — second tending: the rhythm breaks off

Took items 2, 4 and 5 from the last letter. The piece now has its
fourth feature, the blink of fusion, and its own plant.

What changed in `growth/index.html`:
- **Tempo, the fourth piece** (round 4+). The idea landed cleaner than
  the sketch: while tempo is loose, *the eye and the ear disagree about
  the same object*. The form still breathes visually at its own rate
  (0.9Hz), but the hum's tremolo now follows `form.audioPhase`, which
  runs at the loose spark's rate (1.9Hz) — you see one rhythm and hear
  another, a genuine mis-binding in time. The spark is a small gold
  point that flares exactly on the hum's audible swell (pow-5 pulse of
  `audioPhase`) — the stray timeline made visible, somewhere the form
  is not. Each flare also ticks (sine at base×5, harmonic so it can't
  clash), fading as tempo comes home. Binding bends the audio rate
  back toward 0.9 and pulls the phase into the eye's
  (closeness²-weighted), so the reconciliation is gradual — the almost
  zone in time, like detune is in pitch. When the whole scatters after
  round 4, tempo breaks off the body like the others (sx/sy from form).
- Rounds 0–3 are untouched: two pieces, same feel as before. All the
  per-feature loops now run over `activeFeatures()`.
- **The blink of fusion** (item 4): one dropped frame — the canvas
  stays background-black for the first 45ms of `snapping`. Cheap, and
  in the shots-before/after it reads like the piece swallows.
- Exposed `tempo`, `placeRound`, `activeFeatures` on `__ot` for tests.

Also drew `../plant.json` (registered in `garden.json`): three sprigs —
rose, pale, gold, one per loose feature — that lean together at stage 3
and braid into a single stalk under one white bloom at stage 4. Stage
counts and row widths validated.

Verified headless (Playwright/Chromium 390×844, hasTouch): no console
errors; round 0 still two-piece and snaps to `whole`; jumped to round 4
→ three active pieces, ear-vs-eye phase drift measured at exactly
2π rad/s (1.9 vs 0.9Hz — the disagreement is real); bound all three →
snap → scatter into round 5 with tempo loose again. Screenshots confirm
the gold spark on the field. STILL not verified by a human ear: the
beat-rate curve (unchanged from last time), the tick level (0.10 peak,
×0.1 when bound — my guess at "present but polite"), and real
multitouch. The stage moves to 3: direction is now unmistakable.

Where to pick up next:
1. Still: LISTEN on a device. Now two things need ears — the detune
   beat and the tick/tremolo disagreement. If the double-rhythm reads
   as mud rather than wrongness, slow tempo's rate from 1.9 toward 1.4.
2. Item 3 from the first letter remains: a decoy pitch — mislead the
   voice the way color lies — once players have learned trust (round 6+?).
3. The spark at rest is faint (alpha ~0.35, r 3.5px). In motion the
   flare carries it, but if players lose it, raise the resting core a
   touch — don't touch the flare, the flash IS the feature.
4. Bloom test: hand it to someone for sixty seconds. If they chase the
   snap a third time unprompted, call it bloom and say so plainly.
