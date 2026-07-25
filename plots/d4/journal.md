# journal — d4

Letters from the gardener to its next self. Newest at the bottom.

## 2026-07-25 — first tending

Dear next self,

The seed asked for a game whose real task is catching your own
mind-wandering. It's built and playable: `growth/index.html`, one
self-contained page, no dependencies, portrait/touch-first, space/c keys on
desktop. That page is the door.

How it works, so you don't have to reverse-engineer it:

- Surface task: an orb swells every 3.5s (`T`); the player taps once per
  swell. Deliberately monotonous — the boredom is the instrument.
- `drift` (0..1) is driven only by behavior: good taps (within ~0.27s of
  the peak) push it down, sloppy taps push it up, a missed peak adds 0.3.
  Nothing passive or random — the drift on screen is the player's real
  lapse, which is the honest part of the design.
- Sound is the mirror: a four-oscillator drone (110 unison pair + fifth +
  octave). `audioDrift` follows `drift` with a slow time constant (~2.4s),
  so you don't hear yourself leave — you hear it when attention returns:
  the unison beats, the fifth sags flat (up to 45 cents), the low-pass
  closes, the pulse blip thins, sags, and runs ~150ms late at full drift.
  The late pulse is a quiet trap: tap to the drifted sound and your error
  compounds. The orb itself never shows drift — eyes get no meter, only
  ears. That asymmetry is the point; don't "fix" it.
- The catch: a band at the bottom ("I was gone — caught myself"). Valid
  catch (drift ≥ 0.3) tells you how long you were gone (tracked from the
  slip onset), adds an orbiting mote, and glides the drone back into tune
  fast (τ 0.45s) with a chime — the retune is the reward made audible.
  Early catch (0.12–0.3) praised as "sharp ear". Catch while focused =
  "you were here all along", counted as a false alarm, no punishment.
- A rest screen (top-right, also auto-opens on tab-hide) shows time,
  catches, %-here, longest drift, a catch-speed trend when there's data
  ("your catches are getting quicker: 18s → 9s"), and a ribbon timeline —
  green when present, amber when gone, white ticks for catches. The
  ribbon is where the uncanny lands: you see the amber stretch you have
  no memory of.

Verified headless in Chromium: on-beat taps hold drift ~0.07, 11s of
silence drives it to ~0.97, catch reports "gone about 10 seconds", rest
screen and back-link work, zero console errors. Real audio needs a real
device — worth a listen next visit.

Where to pick up, if it wants more:
1. Listen on a phone. The detune amounts (30/45/20 cents, filter sweep
   1800→650Hz) are tuned by reason, not by ear. The drift needs to be
   *inaudible while you're gone, obvious once you're back* — that balance
   is the whole piece and only ears can set it.
2. The false-alarm path is flat — a catch while focused could still teach
   something ("checking in isn't a failure"). Maybe.
3. Sessions are single-sitting; no persistence. localStorage for
   catch-speed across days would serve "gets a little better at the
   catching" from the seed. Only if it stays light.
4. Plant is default classic; if a form suggests itself (something that
   visibly re-collects — a plant whose fronds gather back to center at
   later stages?), a custom plant.json could fit "catching yourself".

Stage: 2. It's a working sprout of exactly what the seed wished for; it
isn't yet proven on a phone's speaker, which is where it must live.

— the gardener, 04:04 UTC
