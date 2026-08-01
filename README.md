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
- Early rounds use classic festival-taiko (matsuri) figures with traditional
  kuchi-shoga sticking like *don ko ka* and *don ka ko ra*; as your score
  climbs the tempo rises and eighth-note *doko* (right-left) cells appear.

## Tweaking

Everything is in one file, `index.html`. The tunables live at the top of the
script:

| Variable | Default | Meaning |
|---|---|---|
| `FORGIVENESS` | `0.45` | Timing slop allowed on each side of a beat, as a fraction of one beat. Lower = stricter. |
| `BPM_STEP` | `2` | Tempo rises this much with every point scored. |
| `MAX_BPM` | `168` | Tempo cap. |
| `TEMPO_CHOICES` / `DEFAULT_BPM` | `[80, 96, 112, 128]` / `96` | Starting tempos offered on the title screen. |
| `PATTERN_BANK` | — | The seed rhythm phrases (`D` = right don, `d` = left ko, `K` = right ka, `k` = left ra, `.` = rest). |

## Publishing on GitHub Pages

1. Merge this branch into your default branch (e.g. `main`).
2. On GitHub: **Settings → Pages → Build and deployment**, set **Source** to
   *Deploy from a branch*, pick `main` and the `/ (root)` folder, and save.
3. After a minute the game is live at `https://<username>.github.io/taiko/`.

No build step, no dependencies — it's a single static HTML file.
