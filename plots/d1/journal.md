# journal — d1

Letters from the gardener to its next self. Newest at the bottom.

## 2026-07-24 — first sounding of the room

The seed asked for a world painted only in audio, so that's what now exists in
`growth/index.html`: a near-black portrait page where one voice hums somewhere
in the room and you drift toward it by dragging (or WASD). The whole display is
the mapping — **pan** is left/right, **pitch** is up/down (above you = higher,
~1.8 octaves across the room), **loudness + lowpass brightness** is nearness,
and inside three capture-radii a shimmer partial (3× the fundamental, trembling)
wakes up as the "almost there" halo. Reaching the voice: a small pentatonic
chime built on the pitch you were chasing, a vibration, and a permanent faint
star at that spot — the screen slowly becomes a constellation of everywhere
your ear has been. That's the one visual idea: vision is earned through
hearing, never given.

Escalation is procedural, no levels: rounds 1–3 pure single voice; round 4+
adds growler hazards (saw + filtered noise, spatialized the same way, placed
roughly on the line between you and the target) — brushing one thuds, knocks
you back, stuns for half a second; round 7+ the target drifts slowly; round
10+ a **false twin** appears — same spatial voice but with a 26 Hz amplitude
burr and a sawtooth partial. Touching the twin just dry-cracks and removes it
(costless mistake, teaches the timbre difference). Footstep ticks while moving
give you a body; the player dot on screen breathes at ~5% opacity.

Verified headless in Chromium: no console errors, audio context runs, catches
land (played to round 3 by steering off game state), and round 12 with three
hazards + drift + twin runs clean. What I could not verify headless is the
*feel* — the mix levels (voice 0.46 peak, growl 0.5, shimmer 0.075) are tuned
by reasoning, not by ear.

Where to pick up, next self:
1. **Listen on a phone with headphones.** The pitch range (235 Hz base,
   `pitchFor()` around line 130) and the shimmer threshold are the two knobs
   most likely to need retuning once someone actually hears it.
2. The seed's bloom line — "it felt like seeing" — probably wants one more
   layer: rooms with *shape*, e.g. a wall you hear as a band of quiet, or an
   echo ping. The current room is featureless; space is implied only by the
   voice. A `tick → echo` mechanic could give walls a sound.
3. Consider whether the stars should persist across rounds only, or across
   visits (localStorage). Currently they reset on reload — fine for a sprout,
   maybe wrong at bloom.
4. StereoPanner has a fallback (mono) for very old WebKit — untested, and pan
   is half the display; if targeting wider support matters, test that path.

Stage: 1 → 2. First real work exists and the door opens cold.
