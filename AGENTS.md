# Woorden spellen — agent notes

License: MIT (`LICENSE`). Copyright line may be updated by the maintainer.

## What this repo is

Static Dutch spelling-practice page: **Web Speech API** (`speechSynthesis`, `nl-NL`) reads words from a hidden list; the user spells during timed silence. No build step, no backend.

## Where the app lives

- **Canonical file for GitHub Pages:** `docs/index.html`
- Edit that file (or keep a local copy in sync). The published site root is the `docs/` folder when Pages is set to **Deploy from branch** with the **`/docs`** folder.

## Behaviour (do not break without intent)

- Word list is in a visually hidden `#words` textarea (no on-screen cheating). **Nieuwe lijst** fills it from `WORD_BANK` (shuffle, no duplicates per round). List length follows the current list length (default 4 on first load).
- Pause length: radios **5 / 7 / 9** seconds (`name="silence"`).
- Status text must **not** reveal the current word (only index / counts).
- `u.rate` is fixed in script (currently `0.95`).

## Constraints

- Speech quality and voices depend on the visitor’s OS/browser; this is not cloud TTS.
- There is no reliable in-browser export to a shareable audio file from `speechSynthesis` alone.

## If you add features

Prefer keeping a single HTML file unless splitting clearly helps. Any new copy should stay Dutch unless the product goal changes.
