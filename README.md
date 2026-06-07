# Wordoban

Wordoban is a small browser game that combines Sokoban-style block pushing with syllable recognition.

The player hears a word, then pushes syllable blocks into the target row in the correct order. Extra distractor blocks are mixed into the board, so the puzzle is about selecting the right syllables as well as arranging them.

## Play

Open `index.html` directly in a browser, or host the repository with GitHub Pages.

Controls:

- Arrow keys or WASD to move.
- On-screen direction buttons for touch input.
- Replay Word to hear the target word again.
- Reset to restart the current puzzle.
- New Puzzle to generate another solvable layout.
- The settings cog opens difficulty controls.

## Settings

The setup panel exposes:

- Word length: 1, 2, 3, or 4+ syllables.
- Board size: 12 to 20 tiles.
- Wall segments: number of wall obstacles.
- Min wall length and max wall length.

Walls are straight horizontal or vertical segments. Generated walls keep space between each other so they do not form corners or joined clusters.

## Words

Words are stored in `assets/words.yaml`, grouped by syllable count:

```yaml
3:
  - word: butterfly
    syllables: [BUT, TER, FLY]
    distractors: [BAT, DER, FLEE, BUTT, TIE]
```

Each entry needs:

- `word`: the word spoken by the browser Speech Synthesis API.
- `syllables`: the correct block sequence.
- `distractors`: extra blocks that do not belong in the answer.

## Assets

The game uses:

- `assets/logo.png`
- `assets/block.png`
- `assets/player.png`
- `assets/background.jpg`
- `assets/words.yaml`

`assets/images.png` and other source images may exist locally as working files, but the game only needs the assets above.

## Technical Notes

Wordoban is intentionally dependency-free:

- Single-page HTML app.
- Embedded CSS and JavaScript.
- Canvas rendering.
- Browser Speech Synthesis for audio.
- YAML word data loaded from `assets/words.yaml`, with an embedded fallback in `index.html`.

Generated levels are checked before play. Correct syllable blocks are scattered away from the target row, distractors are mixed around the board, and the generator rejects layouts that break the intended solution path.
