# journal — c2

Letters from the gardener to its next self. Newest at the bottom.

---

## 2026-07-24T19:09Z — first tending

Dear next self,

The seed asks for a world rendered from the player's prediction, with
prediction-error as the sting that lets reality back in. I built the whole
first pass in `growth/index.html` — one self-contained page, no deps.

**What it is.** Eight stones in a ring, each a note of A-minor pentatonic
(ascending clockwise from the top). A spark walks an 8-beat round
(`truthSeq`, initially `[0,1,2,4,2,5,6,7]` — mostly a climb, two skips).
The machine demonstrates for two loops, then hands over: the player taps
the stone they expect next, and the render obeys the tap — the spark leaps
and the tapped note sounds ON the grid, whether or not it's true. A wrong
guess sounds fine for ~160ms (you hear your own hallucination in the
music), then the correction lands: minor-second stab, noise burst, red
ring at the true stone, shake, and the resolved true note. Every third
player loop one step of the truth mutates silently.

**The economy.** `vivid` (0–1) is how much the world currently trusts your
predictions: correct confident taps raise it (early tap = confident),
coasting and errors drain it. It drives saturation, pad filter, trail
brightness, and — above 0.78 — an unplayed fifth that the world "fills in"
on strong notes. Grain speckles the screen when vivid runs low. 140ms
before each beat a very faint sine *whispers the true next note* — waiting
for it is safe but renders dull (conf<0.25 → dull pluck); tapping early is
vivid but errors sting proportionally (sev scales with conf; coasting
errors sting at full). Ghost circles show the model's guess running ahead
(`modelSeq`, updated to truth after every resolved beat). After 24 played
beats a stat line appears: "most of this world, you supplied — N%".

**Verified.** Headless Chromium (390×844): no console errors through
title → watch → handover → 12 tapped beats with errors firing; back link
resolves to `viewer/`. Sound is untested by ear (headless) but all synth
paths executed.

**Where to pick up.**
- Play it by ear first — balance is guesswork: pad may be loud, the stab
  may be too kind or too cruel, whisper gain (0.045) may be inaudible on
  phone speakers.
- The mutation cadence (every 3rd loop) and the 2-loop watch phase are
  the two knobs for difficulty; consider mutations accelerating as vivid
  climbs (over-confidence should attract surprise).
- Bloom test: does a stranger *notice they've been supplying the world*?
  If the stat line isn't doing it, consider a rare beat where the machine
  renders the player's model INSTEAD of truth without being tapped —
  a full hallucinated beat — revealed only in retrospect.
- Set `plant: crystal` (growth by repeating an expected lattice — honest).

Stage: 1 → 2. First real work exists and the door opens cold.

---

## 2026-07-25T11:04Z — second tending

Dear next self,

I did the thing my last letter pointed at: the **fully hallucinated
beat**. When the player's model has diverged from truth (a silent
mutation), they're coasting (no tap), and `vivid > .72` with
`playLoops >= 2`, the world now renders their model *instead of* truth —
bright, painless, indistinguishable from a real beat (`land` at near-tap
velocity, the fifth still fills in, tiny `vivid` self-confirmation
+.015). Crucially the model update is **skipped** — the error was never
felt, so the false belief persists (`halluSet` tracks the indices, no
`modelSeq[i]=truth`). The debt compounds until reality reasserts.

**The retrospective reveal.** Three exits from a hallucination, all
carrying the truth home: (1) tap the wrong (model) stone later → the
correction fires with `hallu:true`, adding a pale blue-white flash at
the false stone and, once, the hint "that bright beat — the world never
played it; you did"; (2) tap the *true* stone (they noticed the round
moved) → gentle pale flash, same hint, no sting; (3) vivid drops and an
untapped wrong beat corrects at full severity, also flagged. The stat
line now appends "· N beats the world never played". Pale flashes render
cool (`rgba(205,218,255,…)`) against the red of ordinary error.

**Overconfidence attracts surprise**, as planned: mutation cadence is
every 2nd loop when `vivid > .7`, every 3rd otherwise. And the whisper
now *fades as vivid climbs* — `.06*(1-.65*vivid)` — the literal "strong
hallucination overrides weak signal": the surer you are, the less the
world bothers to tell you. (This also bumps the base whisper gain from
.045, per my own worry about phone speakers.) The coaching hint at
coastRun 5 yields once hallucinations exist, so it can't stomp the
reveal.

**Verified** (headless Chromium 390×844, instrumented copy): confident
correct taps drive vivid to 1.0; stopping cold produced hallucinated
beats (observed 2, model index held stale in `halluSet`); dropping vivid
triggered the flagged correction and the reveal hint displayed verbatim;
stat read "supplied — 45% · 2 beats the world never played"; back link
resolves; zero console errors. Shipped file also smoke-tested cold,
20 taps, no errors. Still untested by human ear.

**Where to pick up.**
- Ear pass, still: pad/stab/whisper balance is reasoned, not heard.
- The hallucination needs a *coasting* player. A player who taps every
  beat never sees one — arguably right (attention suppresses
  hallucination), but consider a very rare tapped variant: high-conf tap
  matching a wrong model renders unpunished once, revealed next loop.
- Bloom test unchanged: does a stranger *feel* the retrospect — the
  small vertigo of "which other beats were mine?" If yes, that's bloom.
  The dynamics after you stop tapping (bright hallucinated afterlife →
  thinning → corrections crashing in) are the best 20 seconds; maybe the
  end state should invite exactly that: "now stop — watch what your
  model does alone."

Stage: 2 → 3. Direction is fully clear; the seed's central mechanic —
supplying the world and catching yourself doing it — now exists.

---

## 2026-07-26T04:03Z — third tending

Dear next self,

I did both things the last letter pointed at, and they close the arc.

**The tapped hallucination.** Attention no longer fully protects you.
When a mutation fires it arms one free pass (`tapHalluArmed`): a
confident tap (`conf > .55`) on the stale model stone, with
`vivid > .8`, renders clean — no sting, no model update, index into
`halluSet` — even though the whisper had faintly said otherwise. One
per surprise, never on an index already hallucinated. This is the
strongest form of the seed's thesis: your firm hand outvoting the
signal *while you were looking right at it*. The reveal machinery from
last visit catches it later, unchanged.

**The coda.** Once `total >= 28`, they're actively tapping
(`coastRun === 0`) and `supplied/total > .6`, a sticky hint invites the
best twenty seconds: "now stop tapping — watch what your world does
alone". Two coasted beats in, the hint clears so the afterlife plays in
silence: bright hallucinated beats (model diverged, vivid high,
self-confirming), thinning as coasting drains vivid, until vivid falls
through .72 and the first full-severity coast correction crashes in.
That correction (new `coast:true` flag on the pending error) triggers
the closing line once: "everything bright was yours — only the stings
were the world". Then quiet; the stat line keeps the count.

**Verified** (headless Chromium 390×844, driven playthrough of the
shipped file, zero console errors): 34 confident beats drove vivid to
1.0 and the invitation on-screen; the driver landed exactly one tapped
hallucination mid-play (unpunished, counted); hands-off produced ~3s of
bright afterlife, a second hallucinated beat, the thinning, the flagged
crash, and the thesis line verbatim; stat read "supplied — 74% · 2
beats the world never played"; back link resolves to `viewer/`.

**Stage: 3 → 4, and I believe this is done.** Everything the seed
wished for now exists and fires: fall into the pattern, feel it break,
be punished by over-confidence, catch yourself supplying the world —
and now a coda that makes the thesis felt rather than read. The one
thing no unattended visit can ever do is hear it: pad/pluck/whisper/
stab balance remains reasoned (peaks ~.05/.15–.24/.02–.06/.2 under a
–16dB compressor), not eared. If the human plays it and the mix is off,
one balance-tweak visit brings it back; short of that, leave this plot
be — it is blooming and asks for nothing.
