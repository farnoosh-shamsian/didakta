# Annotation decisions

Project conventions for Didakta annotation of Xenophon. Every annotation session reads this file first and follows it. A session adds a line under "Recurring cases" when it settles a case that keeps coming back. It never changes a decision marked **open**: only the project owner does.

Cite a decision in the reasoning as `[CONV:D3]` or `[CONV:R2]`.

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
- Name the preposition in the reasoning, so the rows can be found and converted once D1 is decided.

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
| R4 | accusative noun with a supplementary participle after a transitive verb of perceiving or knowing (ὁράω, αἰσθάνομαι, οἶδα, καταμανθάνω) → AccObj first, AccSubj second; the participle takes the same CASE, PartSupp and the plain tense (D7) | cyr.1.1.2.s2 #5 ἀγέλας, #9 ἐθελούσας | PartSupp card ("agrees … with the object when the verb is transitive"); SMYTH:2110 | claude-fable-5-2, 2026-11-16 |
| R5 | predicate accusative (the predicate of an accusative subject or object, with εἶναι, ὤν, or a verb of making or calling) → AccDoubl first; AccSubj or AccObj by agreement second | cyr.1.1.4.s3 #12 αὐτόνομα | AccDoubl card (στρατηγὸν αὐτὸν ἀπέδειξε) | claude-fable-5-2, 2026-11-16 |
| R6 | perfect indicative with present meaning (οἶδα, ἔοικα, εἴωθα, δέδοικα) → Perf 0.60, PerfInten 0.35 | cyr.1.1.3.s3 #3 ἴσμεν | SMYTH:1946; CONV:D2 | claude-fable-5-2, 2026-11-16 |
| R7 | δοκέω “think, seem” + infinitive → InfDec; δοκεῖ μοι “it seems good” + infinitive → InfDyn | cyr.1.1.1.s2 #4 καταμεμαθηκέναι | SMYTH:1983; InfDec card | claude-fable-5-2, 2026-11-16 |
| R8 | genitive governed by a verb of separating or keeping off (ἀπέχομαι, ἀπείργω, παύω) → GenSep first, GenVerb second (the decision guide says GenSep; the GenVerb card lists λήγειν τῶν πόνων) | cyr.1.1.2.s3 #24 ὧν | decision guide; SMYTH:1392 | claude-fable-5-2, 2026-11-16 |
| R9 | dative with a word of likeness or sameness (ὅμοιος, ἴσος, ὁ αὐτός, ὁμόγλωττος) → DatVerb 0.55, DatAccom 0.30 | cyr.1.1.5.s1 #9 αὐτῷ | DatVerb card (μικρὸν μεγάλῳ εἰκάσαι); SMYTH:1500 | claude-fable-5-2, 2026-11-16 |
| R10 | prepositional objects with no fitting tag, until D1 is decided (closest tag, 0.60 or less, note “no fitting tag”): περί + gen GenRef; περί, ἀμφί, κατά + acc AccResp; κατά + gen GenSep; μετά + gen GenPart; μετά + acc AccTime; διά + gen GenLoc (of space) or GenSep (of the intermediary); ἀντί + gen GenVal; ὑπέρ + gen GenCaus; ὑπέρ + acc AccSpac; πρό + gen GenSep; ἐπί + gen GenLoc; ἐπί, παρά, πρός, ὑπό, περί + dat DatLoc; ἀνά + acc AccSpac; μέχρι + gen GenLoc; adverbs of place + gen GenLoc. Treated as fitting: ἕνεκα + gen GenCaus; ἄνευ, χωρίς, πλήν, ἔξω + gen GenSep; ἅμα + dat DatAccom; πρός + gen GenSep; νή, μά + acc AccOath | cyr.1.1.2.s1 #4 τούτοις | CONV:D1 | claude-fable-5-2, 2026-11-16 |
| R11 | ἀποκρίνομαι, ἔρομαι (replying, asking) → MidSpee first, MidRecip second | — | MidSpee and MidRecip cards; SMYTH:1726 | claude-fable-5-2, 2026-11-16 |
| R12 | present of a general truth or standing custom → Pres first, PresIter second (D2); PresIter first only when the sentence marks the repetition | cyr.1.1.2.s3 #1 πορεύονται | CONV:D2 | claude-fable-5-2, 2026-11-16 |
| R13 | aorist of a verb of ruling meaning “came to rule, became leader” (ἦρξε, ἡγήσατο, ἐπῆρξε, ἐβασίλευσε) → AorIngr | cyr.1.1.4.s3 #21 ἡγήσατο | COMM:en-holden-1887-books1-2-notes:18 | claude-fable-5-2, 2026-11-16 |
| R14 | article with an ethnic name: plural peoples (οἱ Πέρσαι) → ArtProp; singular standing for the ruler (ὁ Σκύθης) → ArtPart 0.50, ArtProp 0.30 | cyr.1.1.4.s1 #22 ὁ | ArtProp card; SMYTH:1138 | claude-fable-5-2, 2026-11-16 |
| R15 | ἡγέομαι “lead” → MidMent 0.50, MidMotion 0.30 (D3 lists the verb with the mental middles) | cyr.1.1.4.s3 #21 ἡγήσατο | CONV:D3 | claude-fable-5-2, 2026-11-16 |
| R16 | βασιλεὺς Περσῶν, “king of the X” → GenPos 0.55, GenObj 0.35 | cyr.1.2.1.s1 #9 Περσῶν | SMYTH:1297 | claude-fable-5-2, 2026-11-16 |
| R17 | participle in a periphrasis with εἰμί (ᾑρημένοι εἰσίν, εἴησαν ἂν γεγονότες) → PART PartAttr 0.50, PartSupp 0.35; CASE NomPred | cyr.1.2.5.s3 #9 ᾑρημένοι | SMYTH:1961 | claude-fable-5-2, 2026-11-16 |
| R18 | dative with impersonal verbs: δοκεῖ, μέλει, δεῖ → DatExpr (the card's ἔδοξε τῇ βουλῇ); ἔξεστι, πρέπει, προσήκει, συμφέρει → DatVerb 0.60, DatExpr 0.30 | cyr.1.2.15.s4 #13 Πέρσαις | DatExpr card; SMYTH:1467 | claude-fable-5-2, 2026-11-16 |
| R19 | adverbial τι with δεῖ, δέομαι (ἤν τι δέῃ “if at all there is need”) → AccAdv first, AccObj second | cyr.1.2.9.s4 #11 τι | COMM:en-holden-1887-books1-2-notes:31 | claude-fable-5-2, 2026-11-16 |
| R20 | genitive of the charge or penalty with judicial verbs and nouns (δικάζω ἐγκλήματος, ἐγκλήματα κλοπῆς, θανάτου κρίνω) → GenCaus first | cyr.1.2.7.s3 #4 ἐγκλήματος | SMYTH:1375 | claude-fable-5-2, 2026-11-16 |
| R21 | accusative with κελεύω, ἐάω, ἀφίημι + infinitive (the person ordered or allowed) → AccSubj 0.60, AccObj 0.35 | cyr.1.4.20.s2 #11 υἱόν | SMYTH:1972 | claude-fable-5-2, 2026-11-16 |
| R22 | δέομαί τινος, genitive of the person asked → GenSep 0.50, GenVerb 0.45 | cyr.1.3.13.s1 #14 αὐτῆς | SMYTH:1398 | claude-fable-5-2, 2026-11-16 |
| R23 | dative with ἥδομαι, χαίρω, ἄχθομαι (what one is pleased or vexed at) → DatCaus 0.60–0.70, DatVerb second; ἐπί + dative of the ground of a feeling → DatCaus 0.60, DatLoc 0.20 + "no fitting tag" wording under D1 | cyr.1.4.24.s1 #12 ἱπποκρατίᾳ; cyr.1.4.24.s2 #45 θέᾳ | SMYTH:1517 | claude-fable-5-2, 2026-11-16 |
| R24 | ὑπό + genitive of cause (ὑπὸ τῆς χαρμονῆς, ὑπὸ τῆς ἡδονῆς) → GenCaus 0.75, GenSep 0.20; D4 (GenSep) stays for persons as agents | cyr.1.4.22.s1 #11 χαρμονῆς | SMYTH:1698; COMM:en-holden-1887-books1-2-notes:79 | claude-fable-5-2, 2026-11-16 |
| R25 | αἴτιος, συναίτιος + genitive → GenObj 0.50, GenRef 0.30 | cyr.1.4.24.s1 #29 ἔργου | SMYTH:1425 | claude-fable-5-2, 2026-11-16 |
| R26 | ὡς + accusative absolute of a person (ὡς παυσομένους) → PART PartAcc 0.55, PartCirc 0.40; CASE AccSubj 0.50, AccObj 0.20 with note "no fitting tag" | cyr.1.4.21.s3 #15 παυσομένους | SMYTH:2078 | claude-fable-5-2, 2026-11-16 |
| R27 | perfects and pluperfects of ἵστημι and ἐγείρω with present meaning (ἕστηκα, εἱστήκεσαν, ἐγρηγόρει) are treated like R6 | cyr.1.4.19.s8 #15 ἕστηκε | SMYTH:1946 | claude-fable-5-2, 2026-11-16 |
| R28 | τί “why?” → AccCaus 0.60, AccAdv 0.35; ταῦτʼ ἄρα “that is why” → AccCaus 0.60, AccAdv 0.35 | cyr.1.3.4.s4 #1 τί; cyr.1.4.27.s8 #1 ταῦτʼ | SMYTH:1610 | claude-fable-5-2, 2026-11-16 |
| R29 | ἔδει, χρῆν, ἐξῆν without ἄν of an obligation not met → MOOD IndOblig 0.85, IndCount 0.10 | cyr.1.4.27.s11 #3 ἔδει | SMYTH:1774 | claude-opus-5-5, 2026-11-17 |
| R30 | the god sworn by after μά, νή, ναὶ μά → AccOath | cyr.1.4.27.s10 #12 θεούς | SMYTH:1596 | claude-opus-5-5, 2026-11-17 |
| R31 | διὰ χρόνου, διʼ ὀλίγου “after an interval” → GenTime 0.55, GenSep 0.25 (D1 stays open) | cyr.1.4.28.s3 #10 χρόνου | SMYTH:1685 | claude-opus-5-5, 2026-11-17 |
