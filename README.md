# Didakta: Grammar for Annotation

**Didakta Grammar for Annotation** is a localizable grammar reference for the ancient Greek language, designed as a pedagogical resource for annotating syntactic features not covered in treebanks.

## About Didakta

Didakta has been developed by **Farnoosh Shamsian** at Leipzig University, primarily through rearrangement and reformulation of H. W. Smyth's _Greek Grammar for Colleges_ (1920), inspired by Jeffrey A. Rydberg-Cox's _Overview of Greek Syntax_ (2000). It incorporates insights from recent publications such as the _Cambridge Grammar of Classical Greek_ (Emde Boas et al., 2019).

### Link to various versions and translations:

Ferreira, A. D'O. (2024). Didakta Grammar for Annotation—Versão em Português [translated by Anise D'Orange Ferreira]. https://github.com/ProjetosAbertosClassicasDigitais/Didakta-br-portuguese/ (in this repository: [`grammar/portuguese/`](grammar/portuguese/))
Rahimi, F., Shamsian, F., & Smyth, H. W. (2024). Didakta Grammar for Annotation (Kurdish) [Dataset; translated by Farshid Rahimi, Allameh Tabataba'i University, Tehran]. https://doi.org/10.5281/zenodo.11221442 (in this repository: [`grammar/kurdish/`](grammar/kurdish/))
Shamsian, F., & Smyth, H. W. (2023). Didakta Grammar for Annotation (English) [Dataset]. https://doi.org/10.5281/zenodo.11216456
Shamsian, F., & Smyth, H. W. (2024). Didakta Grammar for Annotation (Persian) [Dataset]. https://doi.org/10.5281/ZENODO.11216819

> **Note on vocabulary links.** The versions deposited on Zenodo, and the DOIs
> cited above, link every Greek word to the **Perseus** word-study tool
> (`perseus.tufts.edu/hopper/morph`). That service is legacy Perseus 4
> infrastructure: it rate-limits and returns HTTP 503 under sustained use, so in
> practice the links fail for anyone reading through a chapter. **In this
> repository every vocabulary link has been migrated to
> [Logeion](https://logeion.uchicago.edu/) (University of Chicago)**, which
> parses the inflected form and returns LSJ, Bailly, Pape, Middle Liddell and
> the other lexica it aggregates. The migration covers all formats — PDF, EPUB,
> DOCX, HTML, the split entries and the TEI XML — in every language.
> Citations still point at Perseus, which hosts the texts, but now over HTTPS.
> The Zenodo deposits are unchanged and remain the citable versions of record.

### Links to related publications:

Shamsian, F., Crane, G., & Rahimi, F. (2024, June 5). Adapting Digital Annotations for Teaching Ancient Greek in Persian. DH Benelux 2024. https://2024.dhbenelux.org/wp-content/uploads/2024/05/DHB24_paper_Shamsian_Crane_Rahimi.pdf
Shamsian, F., Crane, G., Rahimi, F., & Ferreira, A. D. (2024). Localizing Ancient Greek Grammar and Annotations with Didakta. DH 2024.

### Key Features

- **Modular Design**: Each section is self-contained and can be used independently without relying on other sections
- **Flexible Organization**: Sections can be rearranged based on learner needs, course requirements, or project specifications
- **Accessibility-Focused**: Simplified language to minimize inaccuracies in machine translation
- **No Positive Language Transfer**: Explains grammatical concepts without assuming knowledge of other languages, particularly important for localization

### Supported Languages

- English
- Persian
- Kurdish (Central Kurdish, Sorani), translated by Farshid Rahimi, Allameh Tabataba'i University, Tehran (see [`grammar/kurdish/`](grammar/kurdish/))
- Brazilian Portuguese, translated by Anise D'Orange Ferreira (see [Brazilian Portuguese edition](#brazilian-portuguese-edition) and her [translator's notes](grammar/portuguese/translator-notes.md))

## Repository Contents

```
grammar/        the Didakta grammar, one folder per language
annotation/     Greek texts annotated with Didakta tags, one folder per text
reader/         the Didakta Reader, a web page for reading the annotated texts
```

### The grammar (`grammar/`)

One folder per language: `english/`, `persian/`, `kurdish/`, `portuguese/`. Each holds the same files:

- `didakta-{language}.md` - Main markdown version of the grammar.
  Cleaned for reuse: hyperlinks and the table of contents are removed, and
  headings are proper markdown (`#`/`##`/`###`) with footnotes preserved.
- `didakta-{language}.xml` - TEI P5 edition, with a per-word vocabulary link on
  every example. Generated from the markdown and the HTML export; see
  [TEI editions](#tei-editions) below.
- `split-entries/` - one markdown file per grammar entry (`AccAdv.md`, `GenPart.md`, …).

The following are downloaded from the Zenodo versions and are the basis of the markdown versions.
Their vocabulary links have been repointed at Logeion
(see [Vocabulary links](#vocabulary-links)); they are otherwise untouched, and
the PDFs keep their original pagination:

- `didakta-{language}.html` - HTML format for web viewing
- `didakta-{language}.epub` - E-book format
- `didakta-{language}.pdf` - PDF version for printing from
- `didakta-{language}.docx` - Microsoft Word format

The Portuguese edition has no Zenodo deposit; its files are built from the
translator's Google Doc instead (see [Brazilian Portuguese edition](#brazilian-portuguese-edition)).

`grammar/didakta-betacode.json` is the betacode-to-Greek mapping recovered from the
original HTML exports, 2,070 forms. It is what each old Perseus URL referred
to, kept so the migration stays reproducible after the betacode itself is gone
from the files.

### Annotated texts (`annotation/`)

One folder per text, each with its annotated treebank (one CSV, one row per word):

- `iliad/`: Homer, *Iliad* 1 (`iliad-book1.csv`), and the earlier Didakta annotation of *Iliad* 2–24 (`iliad-books2-24.csv`, in its older format).
- `odyssey/`: Homer, *Odyssey* 5.
- `persians/`: Aeschylus, *Persians*. The whole text is included; only the first part is annotated.
- `cyropaedia/`, `anabasis/`: Xenophon, annotated by a language model. Each folder also holds the prompt the annotation was made with, and the Greek text, translations, commentaries and treebanks the prompt draws on.
- `reference/`: what all the texts share: the tag list (`didakta-tag-list.csv`), the tag cards, and the grammars the Xenophon prompts cite.

The columns are described in [`annotation/README.md`](annotation/README.md).

### Didakta Reader (`reader/`)

A web page for reading every annotated text word by word, with its tree and Didakta tags. `.github/workflows/reader.yml` publishes it with GitHub Pages at https://farnoosh-shamsian.github.io/didakta/.

## TEI editions

`grammar/<language>/didakta-<language>.xml` (English, Persian, Kurdish, Brazilian
Portuguese) are TEI P5 encodings of the four grammars, validated against `tei_all`. They are generated
from the two published formats together: the text comes from the markdown, and
the link structure from the HTML export.

How the grammar is encoded:

| Content | TEI |
| --- | --- |
| Chapter (a case, tense, voice, mood…) | `<div type="chapter" xml:id="ch01">` … `ch24` |
| Grammar entry (`§GenPart. Partitive`) | `<div type="entry" xml:id="GenPart">` with `<head><label>§GenPart</label> …` |
| Greek example with citation | `<cit type="example">` → `<quote xml:lang="grc">` + `<bibl>` |
| Its translation | nested `<cit type="translation">` → `<quote>` |
| Greek word, linked to Logeion | `<ref target="https://logeion.uchicago.edu/ταῦτα"><w>ταῦτα</w></ref>` |
| Word highlighted in an example | `<w rend="bold">`, or `<hi rend="bold">` outside a quotation |
| Citation, linked to the passage | `<bibl><ref target="…/hopper/text?doc=…">Xen. Anab. 1.2.3</ref></bibl>` |
| Footnote | `<note place="foot" n="7" xml:id="fn-7">`, inline at the point of reference |
| Greek quoted inside running prose | `<foreign xml:lang="grc">`, its words linked as above |
| References | `<back><div type="bibliography"><listBibl>` |

**Entry identifiers are the same in every language**, so the editions line up
entry by entry — `//div[@xml:id='GenPart']` is the partitive genitive in each file.
This makes the TEI versions usable as a parallel corpus, as an annotation
vocabulary (the Didakta tag is the `xml:id`), or as input to a TEI publishing
pipeline. Each file currently holds 24 chapters, 129 entries and ~650 Greek
examples with translations.

### Vocabulary links

The markdown cleanup removed the hyperlinks. The TEI files put them back: every
Greek word is tokenised as a `<w>` and linked to its vocabulary entry, and every
citation is linked to the passage in the Perseus Digital Library.

This covers the Greek quoted in running prose as well as the examples, so the
`<foreign>` phrases are linked word by word too — something the Zenodo exports
never did:

| | examples | running prose | total |
| --- | --- | --- | --- |
| English | 3,309 | 438 (281 phrases) | **3,747** |
| Persian | 3,296 | 424 (327 phrases) | **3,720** |
| Kurdish | 3,311 | 402 (303 phrases) | **3,713** |
| Brazilian Portuguese | 3,313 | 420 (264 phrases) | **3,733** |

plus 648 / 646 / 648 / 642 passage links. All four files validate against `tei_all`.

The Greek is tokenised from the markdown itself, so the vocabulary links do not
depend on the export at all. The export is still read for the citation links, and
examples are matched between the two files by their Greek text rather than by
position; an example the export does not cover keeps its vocabulary links and is
written without a citation link. `E. Fr. 632` and `Men. Sent. 11` have no passage
link because Perseus does not host those texts.

#### Why Logeion, and not Perseus

The export links each word to the Perseus hopper word-study tool. The hopper is
legacy Perseus 4 infrastructure; it still answers an occasional click, but it
rate-limits hard and returns HTTP 503 under sustained use, so a reader working
through a chapter hits dead links. All vocabulary links therefore point at
[Logeion](https://logeion.uchicago.edu/) instead, which parses the inflected form
and returns LSJ, Bailly 2024, Pape, Middle Liddell, Cunliffe, Autenrieth,
Grieks-Nederlands and Μορφώ together with corpus frequency.

The hopper URLs carry the word in betacode, and a few of those transliterations
are wrong in the export itself — this is what previously left `τραγῳδοῖς` and
`πέντε` pointing at the wrong form. (The recovered mapping has it in black and
white: the export encoded `τραγῳδοῖς` as `oagw|doi=s`, writing `o` for `tr`.)
Logeion targets are built from the Greek word as it is printed, so those errors
do not survive the migration. Elided forms are passed through unchanged: Logeion
falls back to the nearest alphabetic form, so `μήτ᾽` lands on the entry for
`μήτε`.

Citations still point at Perseus, which hosts the texts, upgraded from `http` to
`https` (the hopper serves HTTPS but does not redirect to it). Moving citations
to the Scaife Viewer would need a hand-checked `abbreviation → CTS URN` table for
roughly 70 works and has not been done.

#### How the migration was done

The TEI editions carry Logeion links from the start. The files downloaded from
Zenodo were rewritten in place, one format at a time.

The betacode-to-Greek mapping was learned from the HTML exports themselves, where
each link's anchor text is the word as printed, so no link was rewritten on a
guess; anything unresolvable was left alone and reported. That mapping is kept in
`grammar/didakta-betacode.json` so the migration stays checkable now that the betacode is
gone from the files. PDF pagination, EPUB and DOCX structure, and everything
other than the link targets are exactly as published.

## Brazilian Portuguese edition

`grammar/portuguese/` is the Brazilian Portuguese translation by **Anise D'Orange
Ferreira**, who published it in July 2024 at
[ProjetosAbertosClassicasDigitais/Didakta-br-portuguese](https://github.com/ProjetosAbertosClassicasDigitais/Didakta-br-portuguese/).
She made it with the help of DeepL and then corrected and revised it by hand against
the Greek and the English. Her notes on that revision are in
[`grammar/portuguese/translator-notes.md`](grammar/portuguese/translator-notes.md),
copied with attribution from her repository's README, and the edition is described in
[`grammar/portuguese/README.md`](grammar/portuguese/README.md). Unlike the other three
languages it has no Zenodo deposit: every file here is built from the translator's
Google Doc as it stood on 17 November 2026. Its text is the same as the docx, PDF and
EPUB in her repository.

- **Reviewer comments.** The comments on the Google Doc were resolved before the
  files were built. Most record changes the reviewer had already made in the text;
  the one asking for a clearer wording (`§PresPerf`, how the resultative present is
  translated) was applied. Comments that question an entry or ask for new examples
  (`§AorComp`, telic verbs in `§ImpfComp`) are left for a later revision.
- **Corrections.** Only clear errors were corrected, mostly left over from the machine
  translation: citations whose abbreviation had been translated (`E.` for `And.`,
  `Idade.` for `Ages.`), wrong citations (`T. 5.18` for `Dem. 5.18`, `Il. 16.477` for
  `16.482`), a Latin letter for a Greek one (`Αυδὸς` for `Λυδὸς`), passages still in
  English, mistranslated terms (`átonos` for "atelic", `tribunal` for "court(yard)",
  `alvos` for "targeteers") and a few sentences whose meaning had been inverted
  (the indefinite article, the passive voice). The tag `FutPerfInten` is spelt
  `FutperfInten`, as in the other languages. Wording that is merely debatable was
  left as the translator wrote it.
- **Formatting.** Curly quotation marks; arrows, quotation marks and bold restored
  where they were missing or cut a word in two; the table of contents brought in
  line with the headings; footnote references written alike (`CGCG 30.02`).
- **Formats.** The DOCX is the corrected Google Doc, with its links repointed at
  Logeion. The markdown, split entries and HTML are generated from that DOCX, and
  the EPUB and PDF from the HTML, so all six formats carry the same text. The PDF
  is therefore newly typeset, not a Google Docs export.

## Usage

1. **Online**: Use the HTML versions for interactive reading, with a Logeion
   lookup on every Greek word
2. **Offline**: Download the EPUB or PDF formats for reading on e-readers or tablets
3. **Development**: Use the markdown files for editing or integration into other projects
4. **Interchange**: Use the TEI XML files for annotation tooling, parallel-text work, or digital-edition pipelines
5. **Split Entries**: Access individual concepts from each language's `grammar/<language>/split-entries/` folder for focused learning. More coming on that front soon!

## License

Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)
