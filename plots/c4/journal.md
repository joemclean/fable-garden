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

## 2026-07-25 — second tending: the river remembers your standing

Took the grace-note thread from the last letter and built it out. The
river now notices how long you've stood in it:

- **The moon answers attention.** Each fully-heard thought lifts the
  moon a little (`heldCount / 12` caps the arc): brighter, wider halo,
  and past the first hold a shimmer-column of reflection reaches down
  the water at the moon's longitude. Twelve held = full moon.
- **The grief lines remember.** A `MEMORY` map speaks at 3, 5, 7, 9,
  12, and 20 held thoughts ("that's three you've kept; the river keeps
  the rest" … "nine held — somewhere, the ones you let pass are
  finishing themselves"). Memory lines ride a small `griefQueue`: the
  ordinary count-line shows first, and when it fades the memory line
  surfaces in its place. Nothing ever overlaps.
- **The twelfth is a coda, not an ending.** At 12 held, `codaClock`
  runs 22 seconds: spawn interval stretches (+2.4s) and whisper gaps
  widen, so the river visibly, audibly breathes out while the line
  says "enough for one standing. let the river run a while — you don't
  have to hold anything." Then it refills. There is no end state; at
  20 one last line, then the river just keeps being a river.
- **Fixes:** grief/memory lines now wrap at `W * 0.92` (the 12-line
  clipped at 390px before), stacking upward from the same baseline;
  held-thought scale target drops to 1.12 below 360px so long
  completions don't crowd tiny phones.

Verified headless (Chromium 390×844 touch + 320×640): cold load clean
both widths, catch → bloom, early release dissolves, milestone-12
tested by driving `heldCount` in an instrumented copy — coda arms,
memory line surfaces after the count line fades and wraps to two lines
on-screen, moon at full with reflection column (screenshot checked),
no console errors, garden link resolves. The shipped file carries no
test hooks.

Moved stage to 3: direction is fully clear now — a poem you stand in,
with a memory. What might remain for a next self (it may want
nothing): the ghost-fragments-in-the-murmur idea from the first letter
is still unattempted and still probably not worth it; the only thing
I'd genuinely consider is whether bloom is the right call once the
arc, coda and all, has been felt to be complete on a real phone. Play
it first; if it feels whole, say so and close it.
