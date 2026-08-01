# Taiko Says 🥁

A mobile-friendly rhythm game inspired by taiko drumming and Bop It.

**How to play:** a rhythm plays (the "call"), then you must repeat it starting
on the very next beat (the "response"). Tap **inside the drum circle** for the
bass hit (*don*), tap **anywhere outside it** for the rim hit (*ka*). Miss a
hit, hit the wrong drum, or add an extra hit and the game ends. Your score is
the number of phrases you successfully repeat.

- **Beat visualization** across the top shows the pattern and a moving playhead;
  your correct hits light up green.
- **Score** is the big number in the middle of the screen.
- **Title screen** lets you pick the phrase length (2 / 4 / 8 beats, default 4)
  and shows the top-5 high scores for that length (stored locally).
- Early rounds use classic festival-taiko (matsuri) figures like
  *don don ka* and *don ka don ka*; as your score climbs the tempo rises and
  eighth-note *doko* cells appear.

## Tweaking

Everything is in one file, `index.html`. The tunables live at the top of the
script:

| Variable | Default | Meaning |
|---|---|---|
| `FORGIVENESS` | `0.45` | Timing slop allowed on each side of a beat, as a fraction of one beat. Lower = stricter. |
| `BASE_BPM` | `96` | Starting tempo. |
| `BPM_STEP` / `BPM_EVERY` | `5` / `3` | Tempo rises 5 BPM every 3 successful phrases. |
| `MAX_BPM` | `152` | Tempo cap. |
| `PATTERN_BANK` | — | The seed rhythm phrases (`D` = don, `K` = ka, `R` = rest). |

## Publishing on GitHub Pages

1. Merge this branch into your default branch (e.g. `main`).
2. On GitHub: **Settings → Pages → Build and deployment**, set **Source** to
   *Deploy from a branch*, pick `main` and the `/ (root)` folder, and save.
3. After a minute the game is live at `https://<username>.github.io/taiko/`.

No build step, no dependencies — it's a single static HTML file.
