# Taiko Says 🥁

A mobile-friendly rhythm game inspired by taiko drumming and Bop It.

**How to play:** a rhythm plays (the "call"), then you must repeat it starting
on the very next beat (the "response"). The drum and rim are split into left
and right halves: tap **inside the drum circle** for the bass hit (right-hand
*don* / left-hand *ko*), tap **anywhere outside it** for the rim hit
(right-hand *ka* / left-hand *ra*). Left and right count — each note in the
visualization lights up on the half matching the hand. Miss a hit, hit the
wrong drum or side, or add an extra hit and the game ends. Your score is the
number of phrases you successfully repeat.

- **Beat visualization** across the top shows the pattern and a moving playhead
  (long phrases wrap into rows of 8); your correct hits light up green.
- **Score** is the big number in the middle of the screen.
- **Title screen** lets you pick the phrase length (2 / 4 / 8 / 16 beats,
  default 4), a starting tempo (80–128 BPM), the beat division (4th, 8th, or
  16th notes — each beat cell in the visualization shows one slot per
  subdivision so you can see exactly where off-beat hits land), and whether
  the metronome ticks during play. It also shows the top-5 high scores for
  the chosen length (stored locally). The tempo rises with every point.
- **Practice mode** plays the same way but never ends: a miss just forfeits
  that phrase with a gentle buzz and play rolls on. A quit button in the
  corner returns to the title screen. Practice runs don't record high scores.
- Phrases come from a curated library of 4-beat units written in kuchi-shoga
  notation with traditional sticking (*don ko ka*, *doko doko ka*, …), each
  assigned a **difficulty from 1 to 5**. The game serves phrases at your
  current tier — which starts at 1 and rises every 3 points — and shows the
  phrase's difficulty as stars under the beat display. Longer phrase lengths
  chain library units; 2-beat games use unit halves.
- **Dev mode** (button on the title screen) lists every phrase in the library
  with a ▶ preview button and lets you reassign its difficulty (1–5). Choices
  are saved locally as overrides; RESET restores the defaults.

## Tweaking

Everything is in one file, `index.html`. The tunables live at the top of the
script:

| Variable | Default | Meaning |
|---|---|---|
| `FORGIVENESS` | `0.45` | Timing slop allowed on each side of a beat, as a fraction of one beat. Lower = stricter. |
| `BPM_STEP` | `2` | Tempo rises this much with every point scored. |
| `MAX_BPM` | `168` | Tempo cap. |
| `TEMPO_CHOICES` / `DEFAULT_BPM` | `[80, 96, 112, 128]` / `96` | Starting tempos offered on the title screen. |
| `PHRASES` | — | The phrase library: 4-beat units with default difficulties. Notation: `D` = right don, `d` = left ko, `K` = right ka, `k` = left ra, `.` = rest; letters per beat token set its grid (1 = 4ths, 2 = 8ths, 4 = 16ths). |
| `TIER_EVERY` | `3` | The difficulty tier rises every this many points. |

## Publishing on GitHub Pages

1. Merge this branch into your default branch (e.g. `main`).
2. On GitHub: **Settings → Pages → Build and deployment**, set **Source** to
   *Deploy from a branch*, pick `main` and the `/ (root)` folder, and save.
3. After a minute the game is live at `https://<username>.github.io/taiko/`.

No build step, no dependencies — it's a single static HTML file.
