# Woorden spellen — agent notes

License: MIT (`LICENSE`). Copyright line may be updated by the maintainer.

## What this repo is

Static Dutch spelling-practice page. The browser **Web Speech API** (`speechSynthesis`, `nl-NL`) reads words aloud; the user spells during a timed silence. No build step, no backend, no tests, no package manager.

## Where the app lives

- **Canonical app file:** `index.html` at the repository root. Keep a single HTML file unless splitting clearly helps.
- **GitHub Pages:** deploy from the repository root (`/`), not `/docs`. There is no `.nojekyll` and no Jekyll site.

## Behaviour (do not break without intent)

- `WORD_BANK` in the page script is the word source. **Begin opnieuw** (`#play`) always builds a fresh list (shuffle, no duplicates in the round) and writes it into the hidden `#words` textarea. The count comes from **Aantal woorden** (`#wordCount`): 3–`min(10, WORD_BANK.length)`.
- Words do not have to be hard to spell. Ordinary Dutch words belong in the bank alongside longer ones.
- On first load the slider syncs from the default textarea (4 words: appel, bibliotheek, schildpad, ontwikkeling). The label is `"N woorden"`.
- `#words` stays visually hidden (`aria-hidden`, not focusable) so the round is not on screen. Parsing splits on newlines or commas.
- Pause length: `#pauseSec`, **4–10** seconds, step 1, default **7**. The label is `"N seconden"`. Silence runs between words only; the last word has no trailing pause.
- Status (`#status`) must **not** reveal the current word. It shows index and counts only, for example `Luister… woord 2 van 4.` and `Stilte — spellen… (7 s)`.
- **Stoppen** (`#stop`) cancels speech and the silence timer and sets the status to `Gestopt.`
- `u.lang` is `nl-NL`. `u.rate` is fixed at `0.95`.

## Constraints

- Speech quality and voices depend on the visitor’s OS and browser. This is not cloud TTS.
- There is no reliable in-browser export to a shareable audio file from `speechSynthesis` alone.

## If you add features

Any new copy should stay Dutch unless the product goal changes.
