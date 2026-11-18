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
| R31 | διὰ χρόνου, διʼ ὀλίγου “after an interval” → GenTime 0.55, GenSep 0.25; likewise ἐκ παίδων, ἀπὸ παίδων “from boyhood” → GenTime 0.55–0.60, GenSep second (D1 stays open) | cyr.1.4.28.s3 #10 χρόνου; cyr.1.5.7.s1 #16 παίδων | SMYTH:1685; SMYTH:1688 | claude-opus-5-5, 2026-11-17 |
| R32 | participles with παύομαι, διατελέω, περιοράω, φθάνω and σύνοιδα ἐμαυτῷ → PartSupp (with `id` for σύνοιδα); a nominative participle agreeing with the subject gets NomSubj even where the tree labels it PNOM | cyr.1.5.9.s2 #10 λέγοντες; cyr.1.5.11.s1 #20 ὄντες | SMYTH:2098; SMYTH:2108 | claude-opus-5-5, 2026-11-17 |
| R33 | infinitives that no INF tag names (πρίν + infinitive, the explanatory infinitive after a demonstrative) → InfDyn 0.70, InfDec 0.10 with note "no fitting tag" | cyr.1.5.10.s1 #11 κομίσασθαι; cyr.1.4.28.s2 #9 φιλεῖν | SMYTH:2453; SMYTH:1987 | claude-opus-5-5, 2026-11-17 |
| R34 | present indicative of εἶμι and its compounds with future meaning (πρόειμι “I will go ahead”) → Pres, with the future sense in the reasoning | cyr.1.5.14.s6 #7 πρόειμι | SMYTH:1880 | claude-opus-5-5, 2026-11-17 |
| R35 | imperfects of saying and asking in dialogue (ἔφη, ἔφησθα, ἐπηρώτας, ἤλεγχες) → Impf 0.60, ImpfComp 0.30 | cyr.1.6.3.s1 #8 ἔφη; cyr.1.6.12.s2 #29 ἐπηρώτας | SMYTH:1891; CONV:D2 | claude-opus-5-5, 2026-11-17 |
| R36 | the thing taught with διδάσκω, παιδεύω, with or without the person taught → AccDoubl 0.75–0.85, AccObj second; the person taught → AccObj | cyr.1.6.2.s4 #4 ταῦτα; cyr.1.6.31.s1 #26 δικαιοσύνην | SMYTH:1628 | claude-opus-5-5, 2026-11-17 |
| R37 | ὡς + accusative absolute of an impersonal participle (δέον, δεῆσον) → CASE AccAdv 0.45, AccSubj 0.30 with note "no fitting tag"; PART PartAcc 0.90; plain tense with `id` | cyr.1.5.11.s3 #6 δέον; cyr.1.6.12.s5 #29 δεῆσον | SMYTH:2076; SMYTH:2086 | claude-opus-5-5, 2026-11-17 |
| R38 | participle with ἄν standing for a potential optative (λύσαντα ἄν, μαθὼν ἄν, ἐπιμελόμενος ἄν) → plain tense 0.80, the *Noni tag 0.15 | cyr.1.6.1.s3 #13 λύσαντα; cyr.1.6.23.s2 #15 μαθών | SMYTH:1846; CONV:D7 | claude-opus-5-5, 2026-11-17 |
| R39 | supplementary participle with φαίνομαι, φανερός εἰμι, ἐνδείκνυμαι, and the predicate participle with ἀποδείκνυμι, παρέχω, ἔχω, λαμβάνω “catch” → PartSupp (0.85–0.90 with φαίνομαι / φανερός εἰμι, 0.60–0.70 with the others); CASE of the expressed or unexpressed subject or object | cyr.1.6.24.s4 #3 συνηδόμενον; cyr.1.6.25.s1 #18 πλεονεκτοῦντα; cyr.1.6.36.s1 #13 ἁμαρτάνοντας | SMYTH:2143; SMYTH:2107; SMYTH:2096 | claude-opus-5-5, 2026-11-17 |
| R40 | ὡς ἄν, ὅπως ἄν + optative in an object or purpose clause (ὡς ἂν δυναίμην, ὡς ἂν πραχθείη) → OptPoten 0.55, OptSubor 0.40 | cyr.1.6.13.s2 #17 δυναίμην; cyr.1.6.23.s4 #14 πραχθείη | SMYTH:2201; CONV:D6 | claude-opus-5-5, 2026-11-17 |
| R41 | πρός + accusative of an opponent or of the persons one acts towards (πρὸς ἀνθρώπους ἀγωνιστέον, πρὸς τοὺς φίλους ποιεῖν, πρὸς ἀλλήλους) → AccDirec 0.55, AccResp 0.25 with note "no fitting tag" (D1 stays open) | cyr.1.6.9.s1 #14 ἀνθρώπους; cyr.1.6.28.s2 #11 φίλους | CONV:D1 | claude-opus-5-5, 2026-11-17 |
| R42 | χάριν οἶδα “be grateful”: genitive of the thing → GenCaus 0.60, GenObj 0.30; dative of the person → DatVerb | cyr.1.6.11.s1 #30 τούτων; cyr.1.6.11.s3 #17 τούτων | SMYTH:1405 | claude-opus-5-5, 2026-11-17 |
| R43 | ἰάομαι “heal” (middle-only, transitive) → MidIndir 0.50, MidMent 0.25, status check (D3: no type fits) | cyr.1.6.16.s1 #30 ἰῶνται | CONV:D3 | claude-opus-5-5, 2026-11-17 |
| R44 | recurring tree errors in the Cyropaedia: δεῖ tagged imperfect (fix=v3spia---); εἰκός tagged as a participle (fix to the adjective, NomPred or AccDoubl); τεύξομαι, τεύξῃ with the lemma τεύχω (read τυγχάνω; future middle with active meaning → Act); φίλων with the lemma φίλων and a nominative postag (fix=n-p---mg-); Δία with the lemma ζέυς | cyr.1.6.5.s1 #50 δεῖ; cyr.1.6.6.s5 #7 εἰκός; cyr.1.6.10.s8 #3 τεύξῃ; cyr.1.6.3.s3 #3 φίλων | TREE; MORPH | claude-opus-5-5, 2026-11-17 |
| R45 | εἰς, ἀμφί + a numeral or a share, “about, up to” (εἰς μυρίους, ἀμφὶ τοὺς ἡμίσεις, εἰς ἕνα) → AccAdv 0.50, AccDirec or AccResp 0.25–0.30 with note "no fitting tag" (D1 stays open) | cyr.2.1.5.s2 #12 ὀκτακισχιλίους; cyr.2.1.6.s6 #25 ἡμίσεις | CONV:D1 | claude-opus-5-5, 2026-11-17 |
| R46 | ἥκω “have come” → PresPerf 0.70, Pres 0.25 | cyr.2.1.11.s3 #10 ἥκετε | SMYTH:1886 | claude-opus-5-5, 2026-11-17 |
| R47 | the causative middle (ἐδιδαξάμην, ποιοῦμαι ὅπλα “have arms made”, ἀπογράφομαι “have oneself enrolled”) → MidIndir 0.70, with note "no fitting tag" where the causative sense is clear | cyr.1.6.2.s4 #6 ἐδιδαξάμην; cyr.2.1.9.s2 #16 ποιοίμην | SMYTH:1725 | claude-opus-5-5, 2026-11-17 |
| R48 | the relative ὅς, ἥ, ὅ tagged by the tree as the article (ὅ, οἵ, ἥπερ) → fix the postag to p-…, CASE by function, no ART tag | cyr.2.1.17.s4 #4 ὅ; cyr.2.1.21.s2 #23 οἵ | TREE | claude-opus-5-5, 2026-11-17 |
| R49 | ἐπί + dative of purpose or result (ἐπὶ κέρδει, ἐπὶ ζημίᾳ, ἐπὶ βλάβῃ) → CASE DatCaus 0.50, DatLoc 0.30 with note "no fitting tag"; ἐπί + dative of the ground of laughter or anger stays under R23 | cyr.2.2.12.s3 #12 κέρδει, #16 ζημίᾳ, #22 βλάβῃ | PREP:ἐπί; COMM:en-holden-1887-books1-2-notes:154 | claude-opus-5-5, 2026-11-17 |
| R50 | πρός + genitive in oaths and entreaties (πρὸς τῶν θεῶν) → CASE GenSep 0.50, GenCaus 0.30 with note "no fitting tag" | cyr.2.2.18.s5 #6 θεῶν; cyr.2.2.29.s4 #3 θεῶν | PREP:πρός; SMYTH:1695 | claude-opus-5-5, 2026-11-17 |
| R51 | πρός + accusative of what is answered (εἶπε πρὸς τοῦτο, ἔφη πρὸς τοῦτο) → CASE AccDirec 0.50, AccResp 0.35 with note "no fitting tag"; πρός + accusative of the standard (πρὸς ταῦτα “according to these”) → AccResp 0.55, AccDirec 0.25, same note | cyr.2.2.18.s4 #6 τοῦτο; cyr.2.2.31.s3 #6 τοῦτο; cyr.2.2.18.s5 #44 ταῦτα | PREP:πρός; COMM:en-holden-1887-books1-2-notes:158 | claude-opus-5-5, 2026-11-17 |
| R52 | verbal adjective in -τέος / -τέον: the person who must act → DatAgent 0.90; the verbal adjective → NomPred (or AccDoubl in indirect discourse); a retained object → AccObj | cyr.2.2.15.s6 #9 σοι, #11 γέλωτα; cyr.2.2.25.s4 #4 ἡμῖν; cyr.2.2.23.s1 #31 ἐξαιρετέους | SMYTH:1488; SMYTH:2152 | claude-opus-5-5, 2026-11-17 |
| R53 | infinitive with ἄν standing for a potential optative (ψηφίσασθαι ἄν; βελτίους ἂν … εἶναι) → plain tense 0.80, the *Noni tag 0.15, INF by the governing verb (R38 extended to infinitives); a finite verb near ἄν that does not take it stays plain Ind | cyr.2.2.20.s1 #9 ψηφίσασθαι; cyr.2.2.21.s2 #8 εἶναι, #6 ἡγεῖτο | SMYTH:1846; COMM:en-holden-1887-books1-2-notes:159 | claude-opus-5-5, 2026-11-17 |
| R54 | -θη- aorist of a change of state with no agent (φαιδρωθέντα “brightening up”) → VOICE MidSpon 0.60, Pass 0.30 | cyr.2.2.16.s2 #6 φαιδρωθέντα | CONV:D3; SMYTH:1735 | claude-opus-5-5, 2026-11-17 |
| R55 | ὥστε + infinitive giving the content of a vote or proposal (ψηφίσασθαι … ὥστε μὴ … τυγχάνειν; συνερεῖ ὥστε μὴ … εἶναι) → InfDyn 0.70, InfDec 0.20 | cyr.2.2.20.s1 #18 τυγχάνειν, #27 πλεονεκτεῖν; cyr.2.2.22.s2 #18 εἶναι | SMYTH:2271 | claude-opus-5-5, 2026-11-17 |
| R56 | recurring tree errors in Cyropaedia 2.2: the vocative Ἀγλαϊτάδα tagged as an accusative feminine (fix=n-s---mv-, Voc); second-person middles in -ῃ / -ει tagged as third-person active (πείθῃ, περιάγει → fix v2sp…e…); future indicatives tagged as aorist subjunctives (ὠφελήσουσιν, ἀντιπληρώσετε, ἐπιδαψιλεύσῃ → fix v…f…); λογίζῃ after ἤν tagged indicative (fix to the subjunctive) | cyr.2.2.13.s3 #8; cyr.2.2.15.s2 #6, #10; cyr.2.2.28.s5 #19; cyr.2.2.27.s1 #17; cyr.2.2.26.s1 #9; cyr.2.2.15.s3 #17; cyr.2.2.14.s2 #8 | TREE; MORPH | claude-opus-5-5, 2026-11-17 |
| R57 | ἐπί + dative of succession, “after” (ἀνέστη ἐπ’ αὐτῷ; ἐπὶ τούτοις “after them”) → CASE DatTime 0.50, DatLoc 0.30 with note "no fitting tag" | cyr.2.3.7.s2 #4 αὐτῷ; cyr.2.3.22.s4 #9 τούτοις | PREP:ἐπί; COMM:en-holden-1887-books1-2-notes:180 | claude-opus-5-5, 2026-11-17 |
| R58 | military formations: εἰς + numeral (εἰς τέτταρας, εἰς ἕνα “in single file”) → AccAdv 0.45, AccDirec 0.30 (R45 extended); ἐπί + genitive (ἐφ’ ἑνός) → GenLoc 0.50, GenSep 0.25; both with note "no fitting tag" | cyr.2.3.21.s3 #11 τέτταρας; cyr.2.3.21.s5 #12 ἕνα; cyr.2.3.21.s1 #16 ἑνός | PREP:εἰς; PREP:ἐπί; COMM:en-holden-1887-books1-2-notes:179 | claude-opus-5-5, 2026-11-17 |
| R59 | πρός + accusative of a hardship endured (πρὸς λιμὸν καὶ δίψαν καρτερεῖν) → CASE AccResp 0.50, AccDirec 0.35 with note "no fitting tag" | cyr.2.3.13.s1 #15 λιμόν, #17 δίψαν, #20 ῥῖγος | PREP:πρός | claude-opus-5-5, 2026-11-17 |
| R60 | ὡς + genitive absolute giving what is to be known or believed (ὡς ἐμοῦ ἀγωνιουμένου … γίγνωσκε) → CASE GenAbs, PART PartGen 0.90, plain tense 0.80 / *Noni 0.15 with `id`; ὡς + accusative absolute with a personal or pronominal subject (ὡς … οὐδὲν ἐσόμενον) stays under R37 | cyr.2.3.15.s1 #6 ἀγωνιουμένου, #17 ἀξιώσοντος; cyr.2.3.3.s1 #30 ἐσόμενον | SMYTH:2078; SMYTH:2086 | claude-opus-5-5, 2026-11-17 |
| R61 | dative of the agent with a perfect or pluperfect passive (πᾶσι προκέκριται; ἀνθρώποις ηὑρημένα) → DatAgent 0.70–0.80, DatExpr or DatVerb as alternative (R52 extended beyond verbal adjectives) | cyr.2.3.8.s4 #17 πᾶσι; cyr.2.3.14.s1 #13 ἀνθρώποις | SMYTH:1488 | claude-opus-5-5, 2026-11-17 |
| R62 | the thing taught retained with the passive of διδάσκω / παιδεύω (ταῦτα πεπαιδεύμεθα) → AccDoubl 0.55, AccResp 0.35 (R36 extended to the passive) | cyr.2.3.13.s1 #27 ταῦτα | SMYTH:1632 | claude-opus-5-5, 2026-11-17 |
| R63 | recurring tree errors in Cyropaedia 2.3: adjectives and participles that agree with a nominative subject tagged as accusative (γελοῖα, σπουδαῖα, χαλεπά, φερόμενα, ἕκαστα, μαθόντα → fix to the nominative, CASE =head); ἔφασαν tagged aorist (fix=v3piia---, R35); person and number of ἔπαιον, ἐτύγχανον; lemma errors παρίῃ → πάρειμι (εἶμι), ἀπιόντες / ἀπιέναι → ἄπειμι (εἶμι), ἀναιρουμένους → ἀναιρέω; ἰόντων read as the imperative of εἶμι, status `check` | cyr.2.3.1.s1 #5; cyr.2.3.3.s3 #29, #30; cyr.2.3.9.s1 #28, #34; cyr.2.3.20.s4 #7; cyr.2.3.10.s7 #5; cyr.2.3.18.s2 #11; cyr.2.3.22.s2 #5; cyr.2.3.17.s1 #56; cyr.2.3.21.s5 #13 | TREE; MORPH | claude-opus-5-5, 2026-11-17 |
| R64 | ἐν + dative of dress or equipment worn (ἐν τοῖς ὅπλοις, ἐν τῇ Περσικῇ στολῇ, ἐν μεγάλοις φορτίοις) → CASE DatAccom 0.55, DatLoc 0.35 with note "no fitting tag" | cyr.2.4.1.s1 #10 ὅπλοις; cyr.2.4.5.s2 #10 στολῇ; cyr.2.3.14.s1 #28 φορτίοις | PREP:ἐν; COMM:en-holden-1887-books1-2-notes:181 | claude-opus-5-5, 2026-11-17 |
| R65 | διὰ παντός / διὰ πάντων “all down the line” in passing on orders → CASE GenLoc 0.45, GenSep 0.25 with note "no fitting tag"; κατ’ οὐράν “in the rear” → AccSpac 0.50, AccResp 0.30, same note; κατὰ χώραν “in their places” → AccResp 0.50, AccSpac 0.30, same note | cyr.2.4.2.s1 #37 πάντων; cyr.2.4.3.s3 #38 παντός, #32 οὐράν, #26 χώραν | PREP:διά; PREP:κατά; COMM:en-gorham-1856:123 | claude-opus-5-5, 2026-11-17 |
| R66 | μετά + genitive of company or side (τοῖς μετ’ ἐμοῦ; μετὰ τοῦ ἠδικημένου ἔσεσθαι) → CASE GenLoc 0.45, GenSep 0.25 with note "no fitting tag" | cyr.2.4.16.s2 #8 ἐμοῦ; cyr.2.4.7.s3 #18 ἠδικημένου | PREP:μετά | claude-opus-5-5, 2026-11-17 |
| R67 | recurring tree errors in Cyropaedia 2.4: imperfects tagged aorist (παρήγγελλον); aorist imperatives tagged indicative (πύθεσθε → fix v2pamm---); the lemmas σοι (read σύ), κρατύς for κρείττων (read κρείσσων), διΐημι for διιέναι (read δίειμι), εἰσέρχομαι for εἰσῄει (read εἴσειμι); adverbial πολύ and κάλλιστα tagged as subject or object (fix to AccAdv) | cyr.2.4.2.s2 #6; cyr.2.4.8.s3 #9; cyr.2.4.1.s3 #3; cyr.2.4.12.s3 #6; cyr.2.4.3.s3 #18; cyr.2.4.5.s2 #1; cyr.2.4.16.s4 #3; cyr.2.4.17.s3 #1 | TREE; MORPH | claude-opus-5-5, 2026-11-17 |
