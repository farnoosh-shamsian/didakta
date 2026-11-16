# Annotation decisions

Project conventions for Didakta annotation of Xenophon. Every annotation session reads this file first and follows it. A session adds a line under "Recurring cases" when it settles a case that keeps coming back. It never changes a decision marked **open**: only the project owner does.

Cite a decision in the `evidence` column as `CONV:D3` or `CONV:R2`.

## Decisions

**D1 Objects of prepositions: open.** The project owner has to choose between two options:
- tag the function of the prepositional phrase with an ordinary case tag;
- tag every object of a preposition `GBP`, which Didakta's notes define as "words in the oblique cases governed by an adposition".

The Iliad annotations are no guide here: εἰς + accusative is AccObj 236 times and AccDirec 42 times; σύν + dative is DatLoc 40 and DatInstr 28, and never DatAccom.

*Until it is decided:*
- Give the function where a Didakta tag clearly fits:

  | Construction | Tag |
  |---|---|
  | ἐν + dative of place | DatLoc |
  | ἐν + dative of time | DatTime |
  | σύν + dative | DatAccom |
  | εἰς, πρός, ἐπί, παρά, ὡς + accusative of motion towards | AccDirec |
  | ἐκ, ἀπό, παρά + genitive of source or separation | GenSep |
  | ὑπό + genitive of the agent | GenSep (D4) |
  | διά + accusative "because of" | AccCaus |

- Otherwise give the closest tag with certainty 0.60 or less, and write "no fitting tag" in note.
- Always add `PREP:<preposition>` to `evidence`, so that the rows can be converted automatically once D1 is decided.

**D2 Plain or marked tense tags: open.** The prompts say: use the plain tag (Aor, Impf, Pres) unless the sentence shows the marked use. The Iliad annotators used the marked tags much more often: AorIngr 1,811 against Aor 2,841, and ImpfDesc 1,578 against Impf 1,491. So the new data will differ from Homer in a systematic way. *Until it is decided:* follow the prompts. When a narrative imperfect is descriptive or a stative aorist is ingressive, give the marked tag as the second guess.

**D3 Middle-only verbs (media tantum).** These are classified by middle type, following the Didakta cards, which are based on Allan's *The Middle Voice in Ancient Greek*. "Active meaning → Act" applies only to middle forms of verbs that also have an active (future middles such as λήψεται, ἀκούσομαι).
- MidMent: βούλομαι, ἡγέομαι, οἴομαι, ἥδομαι, αἰσθάνομαι, βουλεύομαι (mental activity or process).
- MidSpon: γίγνομαι and its compounds, φύομαι, ἀπόλλυμαι (change of state without an agent).
- MidMotion: verbs of body motion (ἅλλομαι, πέτομαι, ὀρχέομαι, ὁρμάομαι).
- MidRecip: μάχομαι, διαλέγομαι, ἀγωνίζομαι (contending, conversing).
- MidSpee: middle-only verbs of speech (see the card).
- MidIndir: the subject acts for itself (δέχομαι, κτάομαι, πορίζομαι).
- Passive-form aorists of these verbs (ἐβουλήθην) take the same middle type.
- When no type fits (δύναμαι, κεῖμαι, ἐπίσταμαι), give the two closest tags with low certainty and status `check`; record the verb under "Recurring cases" once it is settled.

**D4 Genitive of agent with ὑπό.** GenSep, as in the Iliad annotations, which tag ὑπό + genitive GenSep in most cases. Part of D1.

**D5 Agr and GBP.** Not used until D1 is decided. The Iliad 1, Odyssey 5 and Persians files do use them.

**D6 Moods in subordinate clauses.**
- A subjunctive in a subordinate clause is SubjSubor, including fear clauses (φοβοῦμαι μή + subjunctive).
- An optative there is OptSubor, except:
  - a potential optative with ἄν, which stays OptPoten;
  - a wish, which stays OptWish.
- An indicative there is Ind, except:
  - past indicatives in an unreal condition (both the εἰ clause and the main clause), which are IndCount;
  - past indicatives with ἄν, which are IndCount.

**D7 Indirect discourse.** Infinitives and participles in indirect discourse keep the tense of the direct form and take the plain tense tag (Pres, Aor, Perf, Fut), not the *Noni tag.

## Recurring cases

| Id | Rule | Example | Evidence | Added |
|---|---|---|---|---|
| R1 | γίγνομαι "come about, occur, arise" → VOICE MidSpon | cyr.1.1.1.s1 #4 ἐγένετο | CONV:D3 | claude-opus-5-5, 2026-11-16 |
| R2 | dative of the person who has, with γίγνομαι or εἰμί → DatPos | cyr.1.1.1.s1 #3 ἡμῖν | SMYTH:1476 | claude-opus-5-5, 2026-11-16 |
| R3 | δύναμαι: no middle type fits clearly; still open (MidSpon / Act / MidMent) | cyr.1.1.1.s2 #31 δυναμένους | CONV:D3 | claude-opus-5-5, 2026-11-16 |
