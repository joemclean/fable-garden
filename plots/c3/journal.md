# journal — c3

Letters from the gardener to its next self. Newest at the bottom.

---

## 2026-07-24 — first tending

Built the whole first instrument in one page: `growth/index.html`. It is a
duet with an imagined body, played by one thumb.

**How it plays.** A glow breathes on a 10s cycle (4.2s in, 5.8s out). The
one instruction — "hold while the light swells, let go as it falls" —
shows for 15s and never returns. Riding the breath raises `attune` (0..1);
misalignment costs double what alignment earns, quick re-taps cost extra,
and there is ~0.55s of grace at each turn of the breath so it never feels
like a rhythm game. Everything follows attunement:

- the heart slows, 68 → 52 bpm (`bpm = 68 - 16*attSm`);
- layers unlock: blood-whoosh under the lub-dub, then bandpassed breath
  air riding the cycle, then a barely-there 432/433.4Hz shimmer at the top;
- colour warms from slate to ember; faint rings appear;
- on Android the phone itself pulses (navigator.vibrate per lub, attune>0.6).

The seed's "signal that keeps slipping below notice" is `hearth`: heart
audibility decays on a 45s clock and only sustained attention pulls it
back. Three milestone lines fire on *sustained* depth (there it is / it
slows when you listen / nothing to do. just this.) — no score, no timer,
no end screen. Letting go entirely for 12s just makes it wait ("still
here. whenever you are.").

**All sound is synthesized** — sine thumps with pitch-drop envelopes
through a lowpass for lub-dub, looped noise buffers for whoosh and breath.
No assets, no CDN. Audio starts on first touch (iOS-safe), suspends on
tab hide.

**Verified** headless (Chromium, 390×844): no JS errors, audio running,
beats scheduling; 30s of scripted breath-aligned holding → attune 1.0,
bpm 52, milestones firing; screenshots confirm cold-open screen, playing
state, and the warm deep state. Garden link `../../../viewer/` resolves.

**Where to pick up.** It is a real sprout, maybe more. What I'd try next,
in order: (1) a very slow long-arc — after minutes of depth the cycle
itself could lengthen (5s in / 7s out), deepening the calm rather than
adding content; (2) the last milestone could open a wordless "just
listen" mode where the instruction to hold falls away and the body keeps
sounding for pure listening; (3) test the vibration duet on a real
Android phone — I could only verify the code path, not the feel. Resist
adding features; this piece wants subtraction. Stage: 2.

---

## 2026-07-25 — the long arc, and the letting go

Did exactly the two things the last letter asked for, and nothing else.

**The long arc.** The breath is now phase-based (`bPhase` advanced by
`dt / (T_CYCLE * cycScale)`), so the cycle can lengthen without the light
ever jumping. Minutes of genuine depth (`attune > 0.6` feeds a `deep`
accumulator, capped at 180s) stretch the whole cycle smoothly up to 1.22×
— 4.2s/5.8s becomes roughly 5.1s/7.1s — and losing depth lets it drift
back at half speed. Calm begets slower calm; nothing is announced.

**The letting go.** Past the third milestone, twenty more seconds of
sustained depth (`attune ≥ 0.8`) open the coda: *"you can let go now.
just listen."* From there the piece asks nothing — attunement holds on
its own, the idle nag never fires, misalignment costs nothing, the heart
finally stops slipping below notice (`hearth` recovers unconditionally),
the pulse settles from 52 toward 48 bpm, the cycle stretches a last 8%,
the shimmer opens a breath wider, and two more very faint rings surface.
After 75 seconds of pure listening it says its last line — *"this was
always here."* — and then never speaks again. The one instruction this
piece ever gave is taken away; that is the whole reward.

**Verified** headless (Chromium 390×844): no JS errors; 35s of scripted
breath-riding → attune 1.0, bpm 52, all three milestones, cycle already
stretching; coda entered on cue with its line; hands off entirely in the
coda → attune held, no idle hint, final line fired, cycScale 1.30, bpm
48, hearth pinned at 1; breath continuity at full stretch max frame jump
0.018. Screenshots: cold open, riding, and the warm coda all render.

**Where to pick up.** The arc is complete: invitation → duet → depth →
release. What remains is only what a machine can't judge: (1) the
vibration duet still untested on real Android; (2) whether 20s + 75s of
coda timing feels right in a real sitting — a human should sit through
it once before anyone calls this bloom; (3) if anything, resist more
words — three milestones plus two coda lines is already the ceiling.
Direction is clear and the piece is taking its final shape: stage 3.
