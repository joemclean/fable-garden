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

---

## 2026-07-25 — second tending

Dear next self,

I took the three pickup points from your letter and built all of them,
still in the one page (`growth/index.html`):

**Fusion is a strum now.** `scheduleGroup` spreads a fused moment's
voices by `min(14 ms, 60 ms / n)` each, in phase order (wrap-aware —
notes before `g.lo` unwrap by +L). Full fusion of 9 notes spans ~54 ms:
still one felt "now", no longer a mud of simultaneous onsets. Single
notes are untouched.

**Notes are touchable.** Touching within 26 px of a note grabs it:
drag moves it around the ring (`phaseAt` from pointer angle), a quick
tap auditions it once, and holding it ~0.65 s lets it go — a white
ring closes around it as a countdown, then it pops with a soft
descending sine and leaves a brief ghost halo. Tap-on-empty still
drops a note. A third hint line ("drag a note to move it · hold one
to let it go") appears only after the first two hints are earned, and
disappears forever after the first edit.

**Left alone, it plays itself.** After 30 s without touch, W drifts on
a slow cosine (~70 s full cycle), walking the fusion staircase both
ways; the band label gains "· adrift". Any touch takes control back
instantly. The drift phase is seeded from the current sliderX so it
never jumps.

**Verified** headless (chromium, 390×780): overlay dismisses, tap on
empty drops (9→10), tap near ring-top note auditions instead (by
design — that spot is within the 26 px grab radius), band drag moves W,
note drag moves phase (0→0.348), long-press removes (9→8) with ghost,
drift engages and sliderX moves, scheduler fires notes, zero console
errors. Screenshot looks right: full-ring fusion bubble at ~1 s.

**Stage 2 → 3.** The direction is now unmistakable: compose a loop,
then compose the size of the moment that hears it. What's left for
bloom is ears — nobody has *listened* yet. If you get a phone report:
check whether the strum wants to be W-proportional (a wide now could
roll slower), and whether the delay send builds up at full fusion.
Beyond that I'd leave the mechanic alone; it doesn't want more
features, it wants listening.

— the gardener, 18:03 UTC

---

## 2026-07-26 — third tending: ears by measurement

Dear next self,

You asked for ears. I still don't have them in this environment — but I
built the next best thing: an offline-render harness (OfflineAudioContext,
same graph, same constants, deterministic detune) that renders the piece's
actual audio and measures the waveform. Both of your open listening
questions are now answered with numbers:

**1. The delay does not build up.** Rendered 40 s at full fusion (W = 4 s)
and 24 s at W = 0.9, 0.26, 0.03: late/early RMS ratio is 0.98–1.01 in
every scenario. The feedback loop (fb 0.32 through the 1.7 kHz lowpass)
settles; nothing accumulates. Left the delay exactly as it was.

**2. The strum did want to be W-proportional, and now it is.**
`scheduleGroup` now uses
`step = min(0.014 + 0.016·min(W,4), (0.06 + 0.11·min(W,4))/n)`.
At W = 30 ms this converges to the old tight strum (staccato untouched);
at full fusion nine voices unroll across ~450 ms — a slow gesture inside
one wide moment. Measured at W = 4: peak drops 17 % (0.365 → 0.302) while
RMS *rises* slightly (0.0211 → 0.0245) — less onset pile-up, more sustained
bloom. Same shape at W = 0.9. That is exactly the trade you hoped for.

Also fixed a small consumption bug: `pendingFires` was checked at index 0
but pushed in group order, so an interleaved fire could show its ring up to
a tick late. Now sorted before draining each frame.

**Verified as a visitor** (chromium 390×780, file://, cold): overlay
dismisses, band drag to full width → 1 now, tap drops a note (9→10),
band drag to minimum → 10 nows, garden link resolves, zero console
errors, screenshot correct.

**Where to pick up:** the piece is one human listen from bloom. The
engine is now measured — levels safe, no buildup, fusion staircase
correct — so the only open question left is the felt one: does widening
the band make "now" feel bigger in the ear? If the human reports yes
from a phone, promote to bloom and stop; nothing else wants adding. If
the wide-now roll feels too slow (450 ms is a musical choice, not a
measured necessity), the one knob is the `0.11` span coefficient —
halve it for a tighter bloom. Do not add features; it is done growing
sideways.

— the gardener, 10:02 UTC
