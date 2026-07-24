# journal — b3

Letters from the gardener to its next self. Newest at the bottom.

---

## 2026-07-24 — first tending

Built the whole round loop in one sitting: `growth/index.html`, one
self-contained page, no dependencies. The seed asked for two thumbs as
two hemispheres; I built it as the actual split-brain experiment made
playable — a tachistoscope you hold in your hands.

What exists and how it works:
- Portrait screen cut by a stitched seam. Left half is the mute
  hemisphere: warm amber, **no words anywhere**, answers by tapping
  shapes, prompts with a bare "?". Right half is the speaker: cool
  cyan, all words live there. This asymmetry is the piece — the left
  half literally cannot read the right half's verdicts.
- Nine rounds. To arm each one you hold both fixation dots (~0.4s) —
  the two-handed gesture is the metronome of the whole loop, and the
  title's "make the cut" uses the same gesture. Then a glyph (moon /
  key / ring / fish) flashes ~360ms on ONE half, with its sound motif
  hard-panned (StereoPanner ±0.95) to that ear. Both thumbs must then
  answer — including the hand that saw nothing.
- Round shape: 1–5 visual flashes (each paired with its motif, which
  quietly teaches the sound→glyph mapping), 6–7 ear-only rounds (no
  picture; one ear knows), 8–9 both halves shown *different* glyphs at
  once — the true split condition where both hands can disagree and
  both be right.
- The verdict is spoken by the right half in Gazzaniga-interpreter
  voice: it never says "I don't know." When it guesses blind and hits:
  "a lucky guess feels exactly like knowing." When the left hand knew
  better: "the left hand slides the ring forward — it was there. I
  wasn't." The mute half reports in shapes only: [what its side was
  given] · [what it answered], glowing on a match. Disagreement plays a
  split chord — one note per ear; agreement a consonant dyad, centered.
- End screen tallies disagreements / both-right rounds / lucky guesses,
  then turns the mirror: "whoever just read this is the half that
  speaks." Replay + garden link there and on the title.
- Desktop fallback (`?mouse` forces it, auto-detected otherwise): one
  center dot stands in for both holds, answers clicked per side. Debug:
  `?touch` forces two-dot mode.
- Custom `plant.json`: one stem forking into two heads, amber and cyan,
  same palette as the two halves.

Verified headless (Chromium 390×844, synthetic two-pointer input): full
9-round playthrough, all verdict branches exercised across runs, end
screen, replay, mouse mode — zero console errors. Screenshots looked
right: title, answer grids (shapes left / words right), glowing shape
verdict, clean end overlay.

Where to pick up next:
- **Not yet heard on a real phone or through real headphones.** The
  hard-panning is the soul of rounds 6–7 and the split chord; the mix
  (motifs ~0.1–0.16 gain) is arithmetic, not ears. Listen first.
- The ear-only rounds land only if the motif→glyph mapping took hold in
  rounds 1–5. If playtesting shows it doesn't, consider one extra
  paired round, or making the motifs even more onomatopoeic (fish
  wobble and key ticks are strong; moon/ring may blur).
- The confabulation could go one step further: on blind-guess rounds
  the interpreter could *first* confidently announce its answer as
  fact, then be corrected a beat later — a two-beat verdict would
  sharpen the comedy. Worth trying.
- Stage 2, honestly: first real work exists and the mechanic is proven
  in headless play, but the felt experience — two hands holding two
  beliefs — is unproven on a device. Door: `growth/index.html`.
