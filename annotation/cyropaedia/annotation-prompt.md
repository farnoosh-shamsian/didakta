# Annotation prompt: Cyropaedia

Open a new Claude Code session at the root of the Didakta repository, on this computer, and paste everything below the line. First set BOOKS and MODEL.

---

Annotate Xenophon's _Cyropaedia_ with Didakta tags: for every word, the function of its case, tense, voice and mood in the sentence, as Didakta (a grammar based on Smyth) defines them.

This run: BOOKS = 1 (one or more book numbers), MODEL = the exact model id you are running as.

## Where everything is

Everything you need is in `annotation/cyropaedia/` and `annotation/reference/`.

- **The Didakta tags:**
  - `annotation/reference/didakta-tag-list.csv` is the list; use no other tag.
  - `annotation/reference/didakta-tag-cards.md` (and `.jsonl`) gives each tag's definition, examples and Smyth paragraphs; `annotation/reference/didakta-decision-guide.md` has ordered questions for the hard families.
  - `grammar/english/didakta-english.md` is the full Didakta grammar.
- **The sentences:** `annotation/cyropaedia/sentences.jsonl`, one sentence per line, in text order. Each has:
  - the Greek and the dependency tree, with lemma, postag, head and relation for each word;
  - the Perseus Greek and Miller's Loeb English of its sections;
  - short LSJ entries;
  - commentary notes that quote the sentence, with source and page.
- **Commentaries:** `annotation/cyropaedia/commentary-*.tesseract.txt`, the OCR text of Holden (the main one), Breitenbach, Bigg, Gorham and MacMillan, page-marked `=== page N ===`. `commentary-notes.jsonl` lists every note linked to a sentence.
- **Translations:** `annotation/cyropaedia/translation-*` (Miller, Dakyns, two French), and `greek-english-miller-sections.jsonl` (Greek and Miller paired by section).
- **Treebanks:** `annotation/cyropaedia/treebank-*.xml` (Gorman's hand trees, GLAUx).
- **Grammars and dictionaries:** `annotation/reference/` holds Smyth, Goodwin's _Moods and Tenses_, Gildersleeve and Middle Liddell.
- **Commentary terms:** `annotation/didakta-commentary-terms.md` shows how the commentators' terms ("dative of interest", "Genetiv des Teilungsganzen") correspond to Didakta tags.
- **Project conventions:** `annotation/annotation-decisions.md`; follow them.

## How to work

Work through BOOKS one chapter at a time, in order.

1. **Gather first.** For each sentence, read everything that bears on it before tagging:
   - the Greek in its context, and the tree;
   - all the commentary notes on it (check that a note really discusses the word; open the page in the commentary's `.tesseract.txt` when the note is cut off or garbled);
   - the grammars;
   - the translations;
   - the dictionaries.

   Any other source you have at hand is also fine.
2. **Then annotate** each word on that evidence. A tag must fit the word's form: a genitive gets a Gen* tag, an aorist an Aor* tag.
3. **Save** each chapter's rows to the output file before starting the next. If the file already exists, continue after its last sentence.

## Output

Write `annotation/cyropaedia/annotation-MODEL.csv` (UTF-8, written with a CSV library), one row per word, with these columns:

```
uid,token_id,form,lemma,postag,CASE,CASE_conf,TENSE,TENSE_conf,VOICE,VOICE_conf,MOOD,MOOD_conf,INF,INF_conf,PART,PART_conf,ART,ART_conf,AUT,AUT_conf,reasoning,annotator
```

- **The families:**
  - CASE for nouns, adjectives, pronouns and participles;
  - TENSE, VOICE and MOOD for finite verbs;
  - TENSE, VOICE and INF for infinitives;
  - CASE, TENSE, VOICE and PART for participles;
  - ART for the article;
  - AUT (plus CASE) for αὐτός.
- **Families a word cannot take:** write `—` and leave the `_conf` cell empty. Particles, prepositions, conjunctions and punctuation get `—` everywhere.
- **Tags:**
  - When you are sure, give one tag.
  - When it is uncertain, give up to three, best first, separated by `; `.
- **Certainty:** in the `_conf` cell give one number from 0 to 1 per tag, in the same order (e.g. `DatPos; DatExpr` with `0.70; 0.25`).
- **reasoning:** why you chose these tags. Keep it short for obvious words and fuller for hard ones.
  - Cite the sources in square brackets: `[COMM:<source>:<page>]` for a commentary note (source and page as given in `sentences.jsonl`), `[SMYTH:<§>]`, `[GMT:<§>]`, `[LSJ]`, `[TR]` for the translation, `[TREE]`.
  - When a commentary note informed the choice, quote its decisive words briefly in “…” with the page.
  - Mention a problem with the tree here too.

  The Didakta Reader shows this text next to the tags.
- **annotator:** MODEL.

Do not change other files, and do not commit. At the end, add one line to `annotation/annotation-runs.md` (create it if it does not exist): date, MODEL, books done, number of words.
