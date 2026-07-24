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
