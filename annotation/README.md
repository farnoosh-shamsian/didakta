# Didakta annotation

Greek texts annotated with Didakta tags. There is one folder per text, and each holds its annotated treebank.

```
annotation/
├── iliad/                         Iliad 1, and the earlier annotation of Iliad 2–24
├── odyssey/                       Odyssey 5
├── persians/                      Aeschylus, Persians
├── cyropaedia/                    Xenophon, annotated by a language model, with everything it was based on
├── anabasis/                      Xenophon, likewise
├── reference/                     shared by all texts: the tag list, tag cards, grammars
├── annotation-decisions.md        conventions the Xenophon annotation follows
└── didakta-commentary-terms.md    commentators' terms → Didakta tags; grammar abbreviations
```

## Homer and Aeschylus (`iliad/`, `odyssey/`, `persians/`)

Annotated by hand, one CSV per text, one row per word:

- `iliad/iliad-book1.csv`: *Iliad* 1. The tree is from the Perseus treebank, and the file includes the Persian word alignment and the Persian and Kurdish sentence translations.
- `iliad/iliad-books2-24.csv`: *Iliad* 2–24, in the older format (a single `didakta` column).
- `odyssey/odyssey-book5.csv`: *Odyssey* 5. The sentence ids and the artificial nodes are from the Perseus treebank.
- `persians/aeschylus-persians.csv`: Aeschylus, *Persians*. The whole text is included; only the first part is annotated.

Columns (all but `iliad-books2-24.csv`):

- `sent_id`, `tok_id`, `line`, `form`, `lemma`, `postag`: the word. `postag` is the 9-character Perseus (AGDT) morphology.
- `CASE`, `TENSE`, `MOOD`, `VOICE`, `INF`, `PART`, `ART`, `AUT`: one Didakta tag per family. `Agr` and `GBP` count as CASE. `—` means the word's form cannot take that family; an empty cell means not annotated yet.
- `CASE_alt`, `TENSE_alt`, …: second guesses, best first, separated by `; `.
- A tag may carry a refinement after a dot, e.g. `SubjSubor.purpose`. The part before the dot is the Didakta tag and points to its grammar entry; the part after it narrows the tag and has no entry of its own. So far only `SubjSubor` and `OptSubor` are refined (Iliad, Odyssey), by clause type: `purpose`, `fear`, `conditional`, `temporal`, `relative`, `question` (indirect question), `simile`.
- `status`: `uncertain` when there is a second guess, a `?`, or a clause type that still needs checking.
- `note`: the annotator's notes. Two kinds of note were added later and are not the annotator's:
  - a part starting `CLAUSE:` says why a clause type needs checking; the clause types were filled in from the tree and by reading;
  - a part starting `OLD CODE:` says how a code from an earlier version of the tag list (`In1`, `Subcl4`, `N1`, …) was read as a current tag. Where that reading is a guess, the row is `uncertain`.
- A tag is written only on the word it describes. Where the original sheet repeated it on a particle or preposition (ἄν with a potential optative, μή with an imperative), the note on that word says `with OptPoten`, `with ImprComm`, ….
- `head`, `relation`: the dependency tree (Perseus AGDT style).
- Text-specific columns:
  - `artificial` (Iliad, Odyssey): `elliptic` marks a treebank placeholder for an unexpressed word, usually a verb (form `[0]`, no tags);
  - `fas_align`, `note_kur`, `sentence_persian`, `sentence_kurdish` (Iliad; the sentence translations sit on each sentence's first row);
  - `speaker`, `section` (*Persians*).
- `didakta_raw`: the tag cell exactly as it was in the original spreadsheet.


## Xenophon (`cyropaedia/`, `anabasis/`)

Annotated by a language model working from a fixed prompt. Each work's folder holds that prompt, the annotated treebank it produced, and every text the prompt gives the model: the Greek, the translations, the commentaries and the treebanks.

### In each work's folder

| File | What |
|---|---|
| `annotation-<model>.csv` | **The annotated treebank.** One row per word: its form, lemma and morphology, one Didakta tag per family (CASE, TENSE, VOICE, MOOD, INF, PART, ART, AUT) with a certainty (`_conf`), and the model's reasoning with its sources. The file name gives the model that made it. |
| `annotation-prompt.md` | The prompt the annotation was made with |
| `sentences.jsonl` | What the model sees for each sentence: the Greek with its dependency tree, the Greek and English of its sections, short LSJ entries, and the commentary notes that quote it |
| `greek-text-perseus.xml` | The Greek text (Perseus) |
| `greek-english-<translator>-sections.jsonl` | The Greek and the Loeb English paired section by section |
| `translation-*` | Translations: English (Loeb, Dakyns, Watson) and French |
| `treebank-gorman-hand-*.xml` | Vanessa Gorman's hand-made dependency trees |
| `treebank-glaux.xml` | GLAUx, an automatic parse of the whole work |
| `commentary-*` | The commentaries (see below) |

Commentaries:

- **Cyropaedia:** the OCR text of nine 19th-century school commentaries (`commentary-*.tesseract.txt`, page-marked `=== page N ===`). Holden is the main one, and the others are Breitenbach, Bigg, Gorham and MacMillan. `commentary-notes.jsonl` lists each note that quotes a sentence, with its source and page.
- **Anabasis:** Geoffrey Steadman's born-digital commentaries on Books 1, 3 and 4 (`commentary-en-steadman-*.pdf`). No commentary notes are linked to sentences yet.

## In `reference/`

| File | What |
|---|---|
| `didakta-tag-list.csv` | The tag list: one row per tag, with its category |
| `didakta-tag-cards.md`, `.jsonl` | One card per tag: Didakta's definition and examples, the Smyth paragraphs it cites, and the tags it is confused with |
| `didakta-decision-guide.md` | Ordered questions for the families that are easily confused |
| `seed-gold-xenophon.csv` | Didakta's own Xenophon examples, located in the trees |
| `grammar-smyth-1920-perseus.txt` | Smyth, *Greek Grammar*, with § numbers |
| `grammar-goodwin-moods-tenses-perseus.txt` | Goodwin, *Syntax of the Moods and Tenses* |
| `grammar-gildersleeve-syntax-perseus.txt` | Gildersleeve, *Syntax of Classical Greek* |
| `lexicon-middle-liddell-perseus.xml` | Liddell & Scott, *Intermediate Greek-English Lexicon* |

The full Didakta grammar is in `../grammar/` (English: `../grammar/english/didakta-english.md`). To browse the annotation word by word, use the [Didakta Reader](../reader/).

## What is not here

These stay on the maintainer's computer and are not in this repository:

- the scanned commentaries, grammars and lexica, which were not used for the annotation;
- the full LSJ entries, which are too large for GitHub (the short entries are in `sentences.jsonl`);
- the scripts that downloaded the sources and built these files.

## Sources and licences

| Source | Licence |
|---|---|
| Perseus Ancient Greek Dependency Treebank 2.1 (trees of `iliad/`, `odyssey/`) | CC BY-SA 3.0 |
| Perseus Greek texts, Loeb translations (Miller, Brownson), Smyth, Goodwin, Gildersleeve, Middle Liddell | CC BY-SA |
| Gorman's treebanks | CC BY-NC-SA 4.0 (Gorman 2020, *Journal of Open Humanities Data* 6: 1, doi:10.5334/johd.13) |
| GLAUx | CC BY-SA 4.0 (per text; see `treebank-glaux.metadata.txt`) |
| Steadman's Anabasis commentaries | CC BY-NC-SA 3.0, geoffreysteadman.com |
| Dakyns and Watson (Project Gutenberg); French translations (Wikisource); 19th-century commentaries | public domain |

Gorman's trees and Steadman's commentaries are licensed for non-commercial use only, so the folders that hold them are too.
