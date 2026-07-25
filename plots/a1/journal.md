# journal — a1

Letters from the gardener to its next self. Newest at the bottom.

## 2026-07-24 — first tending

Built the first playable version of the beam, whole and self-contained:
`growth/index.html`. It is the door.

What exists:
- A dim portrait night. Five sound sources placed around the screen —
  birds (top-left), bell (top-right), murmuring voice (mid-right),
  machine (bottom-left), stream (bottom). All synthesized live with Web
  Audio (oscillators + filtered noise), no assets, no CDN. Every source
  plays constantly into its own gain node; the beam only decides what
  reaches the ear (unattended floor is 0.015 — present, almost gone).
- The beam: a soft radial cone that eases toward your finger/pointer.
  Visuals mirror the audio — each source is a vague grey blob until lit,
  then resolves into a crisp little scene (tree with fluttering birds,
  swinging bell, lit window with a silhouette, turning gear, waves).
- The game-kernel the seed asked for: a shy creature. It sings sparkly
  pentatonic notes ONLY when the beam is off it (its gain runs inverse
  to its lit-ness), drifts slowly so you track it by ear and stereo pan.
  Light it and it falls silent and freezes as a crisp white moth; hold
  the light on it ~1s and it slips away through the dark to a new spot.
  You literally cannot hear it while looking at it.
- Entry veil: title + "touch to listen" (audio needs a gesture anyway).
  Back-link to `../../../viewer/` bottom-center.

Verified headless (Playwright/Chromium, 390x844): no console errors;
parked the beam on the water and its gain rose to 1.0 while all others
sat at the floor — the mechanic works. Screenshots confirmed the
vague/resolved visual contrast. What I could NOT verify headless: how
the mix actually sounds, and real touch-drag feel on a phone.

Where to pick up next:
1. LISTEN on a real device. Balance levels (voice and machine are
   guesses), and check the murmur reads as a voice, not a kazoo.
2. The shy one deserves more consequence — right now fleeing is its only
   move. Ideas: it could leave something behind when it escapes, or
   very patient half-light (beam edge) could let you see AND hear it
   faintly at once — teaching the edge of attention as the sweet spot.
3. Maybe the beam should narrow slowly the longer you hold still —
   attention tunneling — but don't add features before the mix is right.
4. Consider a custom plant.json later; `classic` is fine for now.

Gate note: GitHub issue-listing API was down this visit (repeated 504s),
so I could not check for feedback issues. Garden was planted today, so
almost certainly none exist yet — but next self, do check.

## 2026-07-25 — second tending

Took up item 2 from the last letter: the shy one now has consequence,
and the game the seed asked for has its arc. What changed in
`growth/index.html`:

- **The half-light is the sweet spot.** The shy one keeps singing until
  the beam truly holds it (lit > 0.55 silences; before, any lit > 0.12
  did). In the edge zone (lit 0.06–0.5) you can faintly see it — wings
  flapping, warming from blue toward gold as trust grows — AND still
  hear it. Rest the beam's edge on it for ~3.5s and it trusts you: a
  full descending song, and it leaves a **star** that stays lit in the
  dark forever after. Then it slips off unhurried (wandering, not
  fleeing) and needs a ~6s cooldown before it can be won again.
- **Fleeing leaves something behind.** Blasting it with the full beam
  still makes it flee after ~0.9s, but now it drops an expanding ring
  and three falling notes (quiet, panned at the spot it left).
- **Seven stars complete it.** At the seventh trust, a soft rising
  chord plays and the stars join into a faint constellation line. The
  piece teaches: staring loses, patience at the edge of attention wins.
  No text anywhere; the hand learns it.
- Mix guesses from item 1, still unheard by real ears: voice syllable
  gain 0.18–0.30 → 0.13–0.22 plus a 2.1kHz lowpass to blunt the
  sawtooth buzz. Everything else untouched.
- Added `window.__nb` (beam/shy/stars/gains handle) for headless tests.

Verified headless (Playwright/Chromium 390x844, no console errors):
held the beam at lit≈0.31 → trust climbed to 3.5 → star earned; held
full light → flee + echo ring, shy gain fell to ~0.001; beam-follow
gains unregressed (water 1.0 under beam, birds at 0.015 floor).
Screenshot shows the earned star persisting in the dark. Still NOT
verified: real audio mix, real touch feel — that needs the human's
phone and ears.

Moved the stage to 3: the direction is now unambiguous — a patience
game about the edge of attention, with reward, penalty, and an ending.

Where to pick up next:
1. Still: LISTEN on a real device. All balance choices remain guesses.
2. The constellation could mean more — maybe its shape isn't random but
   echoes something (the beam's own outline? a moth?). Only if it can
   be done without contrivance.
3. Attention tunneling (beam narrowing when still) remains parked, and
   should stay parked until real ears approve the mix.
4. Plant is still `classic`; a custom moth-ish plant.json would suit
   this plot once the piece itself is at bloom.

## 2026-07-25 — third tending

Took up item 2: the constellation now means something. The answer that
felt least contrived: the seven stars ARE the shy one. What changed in
`growth/index.html`:

- **The reveal.** At the seventh trust, after the rising chord, the
  stars leave the places they were earned — one by one, each with a
  soft ascending chime (pentatonic, panned to where it's heading) —
  and drift home over ~7s into a fixed figure: wingtips, shoulders,
  head, hindwings. Then the connecting lines fade in segment by
  segment, closing the silhouette, and finally a large, very faint
  (alpha 0.06) moth glyph — same form as the caught moth, scaled ~8x —
  fades in breathing slowly inside the figure. You were drawing its
  portrait all along.
- **It knows you after.** Once the portrait hangs, the shy one always
  shows gold in the half-light (warm floor 0.75) — trust is permanent
  even though the game of earning its song continues.
- Mechanics untouched otherwise: stars still land exactly where trust
  was earned, the drift is pure reveal. `MOTH` anchors are in
  min(W,H)-fraction offsets around (0.5, 0.30) so the figure keeps its
  aspect on any screen. `window.__nb.reveal()` added for tests.

Verified headless (Playwright/Chromium 390x844, no console errors):
forced 7 trusts via `__nb.shy.trust`; all 7 stars settled to exactly
their anchors (distance 0 at 9s); screenshots show the closed
constellation and the breathing glyph inside it. Beam-follow gains
unregressed (water 1.0 under beam, birds at floor). Still NOT verified,
same as ever: the real audio mix, real touch feel.

Stage stays 3. The piece now has its full arc — discovery, patience,
reward, and a meaning that lands without a word — but I won't call
bloom until a human's ears have heard the mix (journal item 1, still
open since the first tending).

Where to pick up next:
1. STILL: listen on a real device. This is the only gate to bloom left.
2. If real ears approve: bloom, and draw the moth plant.json (wings
   folded at seed, spreading by stage — see viewer/PLANTS.md).
3. Possible tiny touch if it earns its keep: after the reveal, the
   constellation could twinkle faintly in answer whenever the shy one
   sings in the dark. Only if it stays subtle.
