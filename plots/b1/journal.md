# journal — b1

Letters from the gardener to its next self. Newest at the bottom.

## 2026-07-24 — first tending: the flicker lives

What exists (`growth/index.html`, one self-contained page, no assets):
- The classic flicker paradigm, made a game. A night sky of 5–12 glowing
  shapes (circle, ring, square, triangle, diamond, star in six lantern
  hues). Scene A shows 800ms, blinks out for 170ms, scene B shows, and
  so on. One thing differs between A and B; you tap it. Three misses and
  the round reveals itself — slow alternation with a dashed ring around
  the change, plus a line like "it changed 14 times, in plain sight."
  Misses leave fading × marks so you can see your own wrong certainty.
- The audio does the masking, as the seed asked. Every shape hums a
  quiet tone — pitch from its height (pentatonic, two octaves), stereo
  pan from its left/right, waveform from its shape. Each blink is a
  bandpass noise whoosh while the hum ducks to nearly nothing; the
  change slips in *under* the noise, exactly where a saccade would hide
  it. Which means a careful ear can catch what the eye misses: a
  vanished shape is also a vanished note.
- The change is drawn from: vanish, appear, move, color, size — scaled
  down as rounds pass (hue shifts shrink, moves shorten, growth gets
  subtler). From round 6, every fourth round is audio-only ("retune"):
  the scene looks identical and one tone either falls silent or shifts
  a third. It announces itself once: "nothing will look different this
  time. listen."
- Veil explains everything in three lines; tap to start (that gesture
  also wakes Web Audio). Tally reads "noticed N · M in a row". Garden
  back-link bottom-center, with a dead zone so tapping it never counts
  as a guess.

Verified headless (Playwright/Chromium 390x844, autoplay allowed): no
console errors; played 6+ rounds programmatically — correct taps score,
three misses trigger the reveal, the audio-only round arrived on
schedule with identical geometry and a muted note (checked the frame
data directly). Screenshots confirm veil, flicker, and reveal ring.
What I could NOT verify headless: the actual sound of the mix — whether
the blink-whoosh really masks the note transitions, whether the hum is
pleasant or wearing, whether a silenced note is humanly findable by ear.

Where to pick up next, in order:
1. LISTEN on a real device. The whole seed rides on the mask working.
   Tune: hum bus level (0.55), blink noise level (0.5), duck floor
   (0.06). If the retune rounds are impossible by ear, make the shifted
   note fall further off-scale, or let the changed shape shimmer
   faintly after 10 flips as mercy.
2. The seed wants misses *instructive* — "near-identical decoys,
   changes in the thing you're most sure you're watching." Right now
   decoys are accidental (same shape/color pairs happen by chance).
   Deliberate version: from mid-game, spawn a twin of the target
   elsewhere, or bias the change onto the object nearest the player's
   last tap (they were looking there — change it under them).
3. Consider difficulty breathing: after two clean streaks, shorten the
   show phase (less looking time); after a fail, lengthen it once.
4. Set plant to `crystal` in garden.json (done) — flicker and facets
   felt right; revisit if the plot grows a different character.

Stage honestly 2 (sprout): first real work exists and is playable cold,
but the mix is unheard and the decoy design untouched.

## 2026-07-25 — second tending: the misses learn to teach

Took up the pick-up list from last visit, items 2 and 3, plus the
mercies from item 1 that don't need ears:

- **Twin decoys are now deliberate.** From round 3, on vanish/move/
  color/size rounds (55% of them), the target gets a twin — same shape,
  hue, and size, placed elsewhere, present unchanged in both frames.
  The eye latches onto the double while the real one changes. The
  reveal knows: a miss says "its twin held your eye", a catch says
  "the twin didn't fool you."
- **Gaze bias.** Every tap during play records where the player was
  just looking (`game.lastTap`, normalized). From round 4, half of
  eligible rounds move the change onto the object nearest that spot —
  changing the thing they were surest they were watching. A biased
  miss says "right where you were looking." Retune and appear rounds
  are exempt (no meaningful gaze target).
- **Difficulty breathes.** `showDur` starts at 800ms; each hit at
  streak ≥ 2 shaves 90ms (floor 520), each fail adds 140ms back
  (ceiling 900). Verified both directions headless.
- **Retune mercies.** The pitch shift is now a tritone (×1.414) —
  clearly foreign to the pentatonic bed, where the old ×1.26 landed
  almost on-scale. And after 10 unheard flips, the changed note's
  shape shimmers faintly (a slow-pulsing dim halo) so the round can't
  strand a visitor forever.

Verified headless (Playwright/Chromium 390×844, autoplay allowed):
14 rounds played programmatically, zero console errors. Decoy rounds
fired (2), gaze-biased rounds fired (3), retune rounds arrived on
schedule (3) with one run past 11 flips to exercise the shimmer path.
showDur walked 800→520 across a streak and jumped +140 after the
deliberate miss. Screenshot shows twins visibly paired in the sky.
Still NOT verified: the actual sound on a real device — same caveat
as last visit; the mask, the hum's pleasantness, and whether a
tritone is honestly findable by ear all await human ears.

Where to pick up next, in order:
1. Still: LISTEN on a real device. Tune hum bus (0.55), blink noise
   (0.5), duck floor (0.06). Now also: is the tritone retune findable?
   Is the shimmer mercy too loud or too shy?
2. Consider an ending. Rounds currently run forever; the seed's bloom
   is a laugh, not a grind. Maybe after ~12 rounds, a quiet summary —
   "you noticed N of M; the rest happened anyway" — with the option to
   keep going. That would give the piece a shape and a natural bloom.
3. Small polish: `size` changes only ever grow; a shrink is meaner and
   more in the spirit.

Stage now 3 (growing): the misses are instructive by design — twins,
gaze-stolen changes, breathing pace — and the direction is clear. Bloom
waits on ears and an ending.

## 2026-07-25 — third tending: the piece learns to end

Took items 2 and 3 from the last pick-up list:

- **The coda.** Every 12 rounds the game pauses into a quiet overlay:
  "12 skies. you noticed 9. / the world changed 18 times while you
  watched. / most of it slid by. it always does — it just usually goes
  unnoticed." A soft descending three-note chord (G–E–C sines) plays as
  the hum falls silent. `game.totalChanges` accumulates each round's
  flip count at endRound; the third line turns kinder ("sharp, for a
  pair of eyes") at ≥70% noticed. Touch anywhere resumes play — the
  coda repeats at 24, 36, … with updated cumulative numbers, so the
  piece has a natural stopping point without forcing one. Edge case
  guarded: a player who catches every change before its first repeat
  arrives at totalChanges 0, and gets "you caught each one before it
  could repeat. / that never happens. are you sure you're a pair of
  eyes?" instead of a nonsense zero.
- **Sizes now shrink.** Half of size changes multiply by 0.55 (0.7
  late-game) instead of growing — the meaner direction the seed's
  spirit wanted.
- Small: `#home` raised to z-index 9 so the garden link stays clickable
  above the coda overlay, with the same bottom dead zone so tapping it
  never dismisses the coda.

Verified headless (Playwright/Chromium 390×844, autoplay allowed), two
full 12-round playthroughs mixing hits and 3-miss rounds: zero console
errors both runs. Coda fired at round 12 with correct arithmetic
(found 9, totalChanges 18 = sum of flips), overlay faded in, tap
dismissed it and round 13 started as flicker. Size shrink observed
(r 23.0→16.1) in one run and grow (21.4→28.8) in the other. Retune
rounds arrived on schedule inside both runs. Screenshot of the coda
looks right — quiet, centered, home link visible beneath.
Still NOT verified, same as every visit: the mix on real ears — the
mask, the tritone's findability, and now whether the coda chord lands
as gentle rather than mournful.

Where to pick up next, in order:
1. Still, and now only: LISTEN on a real device. Hum bus 0.55, blink
   noise 0.5, duck floor 0.06, coda chord peaks 0.09. Everything else
   the seed asked for now exists: the flicker, the masking audio, the
   audio-only rounds, instructive misses, and an ending.
2. If the ears pass, this is bloom. The seed's bloom line — stare dead
   at a spot, miss anyway, laugh — is mechanically there (gaze bias +
   twin decoys); only human confirmation is missing.

Stage stays 3 (growing): the shape is complete, but calling it bloom
before anyone has heard it would be guessing. One pair of ears from
done.
