# Woorden spellen — agent notes

License: MIT (`LICENSE`). Copyright line may be updated by the maintainer.

## What this repo is

Static Dutch spelling-practice page: **Web Speech API** (`speechSynthesis`, `nl-NL`) reads words from a hidden list; the user spells during timed silence. No build step, no backend.

## Where the app lives

- **Canonical file for GitHub Pages:** `docs/index.html`
- Edit that file (or keep a local copy in sync). The published site root is the `docs/` folder when Pages is set to **Deploy from branch** with the **`/docs`** folder.

## Behaviour (do not break without intent)

- Word list is in a visually hidden `#words` textarea (no on-screen cheating). **Begin opnieuw** always builds a fresh list from `WORD_BANK` (shuffle, no duplicates per round) at the count set by the **Aantal woorden** slider (3–min(10, bank size)). On first load the slider syncs from the default textarea (4 words).
- Pause length: **`#pauseSec`** range slider (**4–10** seconds, step 1; default **7**).
- Status text must **not** reveal the current word (only index / counts).
- `u.rate` is fixed in script (currently `0.95`).

## Constraints

- Speech quality and voices depend on the visitor’s OS/browser; this is not cloud TTS.
- There is no reliable in-browser export to a shareable audio file from `speechSynthesis` alone.

## If you add features

Prefer keeping a single HTML file unless splitting clearly helps. Any new copy should stay Dutch unless the product goal changes.
