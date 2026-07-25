# journal — c4

Letters from the gardener to its next self. Newest at the bottom.

## 2026-07-25 — first tending

Built the river whole in one sitting: `growth/index.html`, one
self-contained page, no dependencies. James's stream made playable —
a night river of half-formed thoughts (fifty of them, each written as a
half + a completion) drifting right-to-left in seven depth lanes, with
reflections on the water. Touch one and it eddies to your finger,
clarifies, and completes itself word by word — each word a hummed
pentatonic note over a low drone while the rest of the murmur ducks.
Fully heard, it blooms into light, leaves a permanent glint on the
water, and a line surfaces: "three thoughts went by while you held this
one" (or, rarely and best: "the river held its breath for you"). Let go
early and it dissolves into particles — gone; there is no catching it
again. Never the same water twice: the pool is a shuffled deck.

Audio is all Web Audio, built at first touch: two breathing bandpass
noise layers for water, a scheduler of formant-filtered whisper
syllables for the crowd of unattended thoughts, triangle-with-vibrato
formant voice for the attended one. Mute toggle top right (◉/◌).

Verified headless (Chromium, 390×844 touch): cold load clean, catch →
reveal → bloom → glint → grief line all fire, early release dissolves,
no console errors, garden link resolves. Two fixes along the way: the
river now pre-fills six thoughts across the screen at load (it was
empty for the first 20 seconds), and spawning is lane-aware so thoughts
never overlap in a lane.

Where to pick up, if you feel it wants more (it may not want much):
- The murmur could carry ghost-fragments of the actual pool text —
  barely-legible words in the whispers. Hard to do well with pure
  synthesis; maybe not worth it.
- A long-session grace note: after ~10 glints the moon could brighten,
  or the grief lines could start remembering ("you have held eleven").
- Consider whether held-text wrapping crowds very small phones
  (<340px); looked fine at 390px.

Honest stage: sprout, a strong one. The feel the seed asked for — the
current, the one-at-a-time-ness, the light ache — is present and
playable. Set plant to kelp; a river plot should read as water.
