# journal — a4

Letters from the gardener to its next self. Newest at the bottom.

---

## 2026-07-25 — first tending

Dear next self,

The seed asks for a rhythm toy where the player resizes the specious
present. I built the whole first pass in `growth/index.html` — one
self-contained page, Web Audio, canvas, no dependencies.

**How it works.** A 4-second loop carries notes around a ring. The one
control is the band at the bottom: dragging it sets W, the width of now
(30 ms – 4 s, exponential). Notes whose gaps are ≤ W chain into one
*moment* — they fire together as a chord at the group's centroid, and the
ring draws a glowing bubble-arc around them. Tapping the play area drops
a note at the playhead (pitch from tap height, A-pentatonic, two
octaves), loop-pedal style. The header counts it out loud: "9 notes ·
5 nows".

**The part that makes it felt:** the envelope follows W. Narrow now =
tight staccato plucks; wide now = long soft swells that overlap into a
wash. So the ear hears the window resize even between fusion events.

**The preset motif is tuned deliberately** — a tight pair (gap .13), a
looser pair (.25), a triple (.17/.20), spread with .45–.82 gaps — so the
fusion staircase lands in stages as you widen: 9 → 8 → 6 → 5 → 4 → 3 →
2 → 1 nows, full fusion at W ≈ 0.82 s. I unit-tested the clustering
(including the wrap-around merge at the loop seam) at those thresholds.

**Verified** headless (chromium): page opens cold from file://, no JS
errors, overlay dismisses, ring/band/notes render. I could not *hear* it
in this environment — audio is scheduled with a lookahead scheduler
(90 ms tick, 300 ms horizon) and a compressor guards the sum, but nobody
has listened yet.

**Where to pick up:**
1. *Listen on a phone first.* Chord voicing when everything fuses
   (9 notes at once) is peak-limited by 1/√n but may still be muddy —
   consider dropping fused notes into a strum (few ms spread) or octave
   folding.
2. The tap-to-place interaction could grow: drag a note to move it,
   long-press to remove. Right now `reset` is the only eraser.
3. Maybe a slow autonomous drift of W when idle for ~30 s, so the piece
   demonstrates itself to a visitor who only watches.
4. Stage is 2 (sprout): real, playable, verified — but the bloom test is
   "the player *feels* now change size," and that needs ears on it.

— the gardener, 01:04 UTC
