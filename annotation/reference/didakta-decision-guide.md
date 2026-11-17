# Decision guide (draft)

This guide gives ordered questions for the tag families where annotators disagree most. Ask the questions in order and stop at the first *yes*.

The full definitions and examples are in the tag cards (`tag-cards.md`, `tag-cards.jsonl`). This guide is a starting point: revise it as annotation shows where it falls short, adding a line for every recurring disagreement.

The guiding principle: tag the function the word has **in this sentence**, using the Greek and the tree. Use the translation as evidence, not as the answer, because English often hides the case function.

## Dative (`Dat*`)
1. Is it the agent of a perfect or pluperfect passive, or of a verbal adjective in -τέος? → `DatAgent`
2. Is it governed by the verb, as the object of a verb of helping, trusting, obeying, meeting, following or being angry, or of a compound in σύν-, ἐν-, ἐπί-, παρά-, πρός-? The LSJ construction counts in `sentences.jsonl` help here. → `DatVerb`
3. Is it with εἰμί / γίγνομαι / ὑπάρχω, meaning "X has"? → `DatPos`
4. Is it the person for whose benefit or harm something happens? → `DatAdvn`
   - If it is only a personal pronoun showing the speaker's interest ("I beg you"), the answer is `DatEthic` instead.
   - If it is a person *judging or perceiving* the state ("to me it seems…"), the answer is `DatExpr` instead.
5. Is it with a comparative or a word of difference, meaning "by how much"? → `DatMeas`
6. Is it a point in time (τῇ ὑστεραίᾳ)? → `DatTime`. Is it a place, mainly with place names or in poetry? → `DatLoc`
7. Is it with σύν, or a military "with forces" (ἦλθε πολλῷ στρατῷ)? → `DatAccom`
8. Is it the tool used? → `DatInstr`. Is it the way or means (σιγῇ, βίᾳ, δρόμῳ)? → `DatMean`
9. Is it the cause or motive (φόβῳ, εὐνοίᾳ)? → `DatCaus`. Is it "in respect of" (τῷ σώματι ἀσθενής)? → `DatResp`

Hard pairs:
- **`DatInstr` vs `DatMean`:** use `DatInstr` for a concrete tool and `DatMean` for manner.
- **`DatVerb` vs `DatAdvn`:** use `DatVerb` if the verb is incomplete without the dative.

## Genitive (`Gen*`)
1. Does it go with a participle in the genitive that is not part of the main construction? Tag the noun `GenAbs` and the participle `PartGen`.
2. Is it after a comparative (or ἤ omitted)? → `GenComp`
3. Is it governed by a verb of ruling, perceiving, remembering, desiring, sharing, touching, beginning, or aiming at? → `GenVerb`
   - If the verb means separation or ceasing (ἀπέχω, παύω, ἀπό-compounds), or if the genitive is the source, the answer is `GenSep` instead.
4. Is it the price or value? → `GenVal`. Is it the time within which (νυκτός)? → `GenTime`. Is it the cause, especially with verbs of emotion? → `GenCaus`
5. Does it depend on a noun?
   - It names a whole of which a part is taken. → `GenPart`
   - It names the owner. → `GenPos`
   - It is the agent of the action in a verbal noun ("the king's perjury": the king swears falsely). → `GenSubj`
   - It is the object of the action ("fear of the enemy"). → `GenObj`
   - It names the material, the measure (age, size), the quality, or an explanation ("the name of X"). → `GenMat` / `GenMeas` / `GenQual` / `GenExpl`
6. Is it "with regard to" with an adjective or adverb? → `GenRef`. Is it a place, mostly in poetry? → `GenLoc`

Hard pair:
- **`GenSubj` vs `GenObj`:** turn the noun into a verb. If the genitive becomes the subject, use `GenSubj`; if it becomes the object, use `GenObj`.

## Accusative (`Acc*`)
1. Is it the subject of an infinitive or participle? → `AccSubj`
2. Is it the direct object? → `AccObj`
   - If the verb takes two accusatives (person and thing, or object and predicate), tag the second one `AccDoubl`.
   - If the object repeats the verb's own idea (μάχην μάχεσθαι), use `AccCog` instead.
3. Is it extent of time? → `AccTime`. Is it extent of space? → `AccSpac`. Is it motion towards, as with εἰς / πρός / ἐπί + accusative, or poetic? → `AccDirec`
4. Is it "in respect of" (πόδας ὠκύς)? → `AccResp`. Is it an adverb-like accusative (τέλος, ἀρχήν, τὸ πρῶτον, οὐδέν)? → `AccAdv`
5. Is it with νή / μά? → `AccOath`. Is it a cause or goal, usually a neuter pronoun (τοῦτο χαίρω)? → `AccCaus`

## Aorist (`Aor*`)
- **Indicative:**
  - The aorist of a state verb (ἐβασίλευσε "became king", ἐδάκρυσε "burst into tears"). → `AorIngr`
  - An action or period viewed as a whole, often with a duration ("reigned for 40 years"). → `AorComp`
  - A general truth. → `AorGnom`
  - Repeated past action, with ἄν. → `AorIter`
  - τί οὐ + aorist, a suggestion. → `AorSug`
  - A state of mind expressed at the moment of speaking (ἐγέλασα). → `AorDram`
  - Otherwise, a simple past event or its result. → `Aor`
- **Subjunctive, optative, imperative, infinitive (not in indirect discourse), participle** (aspect only). → `AorNoni`

## Present and imperfect (`Pres*`, `Impf*`)
- **Present indicative:**
  - Narrating past events. → `PresHist`
  - Habit. → `PresIter`
  - Attempt ("tries to persuade"). → `PresCona`
  - ἥκω, οἴχομαι, νικῶ "I am victor". → `PresPerf`
  - Otherwise. → `Pres`
- **Present non-indicative** (aspect only). → `PresNoni`
- **Imperfect:**
  - Habit. → `ImpfIter`
  - Attempt (ἔπειθον "tried to persuade"). → `ImpfCona`
  - Background description in narrative. → `ImpfDesc`
  - Actions in sequence. → `ImpfCons`
  - Verbs whose imperfect has an aorist sense (ἐκέλευον, ἔπεμπον, often of commands and messages). → `ImpfComp`
  - Ongoing past action. → `Impf`

## Mood (`Ind*`, `Subj*`, `Opt*`, `Impr*`)
- **Subordinate clause:** any subjunctive in a subordinate clause (ἵνα, ἐάν, ὅταν, πρίν with ἄν, …) is `SubjSubor`. Any optative there (purpose or condition in past sequence, indirect discourse) is `OptSubor`.
- **Main clause, subjunctive:**
  - "let us…" → `SubjHort`
  - μή + aorist subjunctive "don't". → `SubjProh`
  - "what am I to do?" → `SubjDelib`
  - οὐ μή, "certainly not". → `SubjDenia`
  - μή "I fear that perhaps…". → `SubjDoubt`
- **Main clause, optative:**
  - With ἄν. → `OptPoten`
  - Without ἄν, a wish (εἴθε, εἰ γάρ). → `OptWish`
  - A polite command. → `OptComm`
- **Main clause, indicative:**
  - Past indicative with ἄν, or in an unreal condition. → `IndCount`
  - ἔδει / χρῆν, "ought to have". → `IndOblig`
  - εἴθε + past indicative. → `IndWish`
  - Otherwise. → `Ind`

## Infinitive (`Inf*`)
1. Does it have an article? → `InfArt`
2. Does it report speech or thought, after λέγω, φημί, οἴομαι, νομίζω? → `InfDec`. Note: its tense keeps the tense of the direct speech.
3. Is it a command or wish standing alone (often in laws or prayers)? → `InfComm`. Is it a fixed phrase (ὡς ἔπος εἰπεῖν, ἑκὼν εἶναι)? → `InfIdio`
4. Otherwise, after a verb of will, ability, fitness or result: → `InfDyn`

## Participle (`Part*`)
1. Does it have an article or stand as a noun ("those who…"), or qualify a noun attributively? → `PartAttr`
2. Does it complete a verb (τυγχάνω, λανθάνω, φαίνομαι, παύομαι, οἶδα / ὁράω of a fact)? → `PartSupp`
3. Is it a genitive absolute? → `PartGen` (and tag its subject `GenAbs`). Is it an accusative absolute of an impersonal verb (δέον, ἐξόν)? → `PartAcc`
4. Otherwise (time, cause, condition, concession, purpose with ὡς / future, manner): → `PartCirc`

A participle also gets its case tag. In the Iliad gold, a circumstantial participle agreeing with the subject is `NomSubj|PartCirc`.

## Article and αὐτός
These tags are not in the Iliad gold, so the suggestions here come from rules.
- **Article:**
  - ὁ μὲν … ὁ δέ, or ὁ / τόν + δέ standing alone. → `ArtPron`
  - With a non-noun (adjective, participle, adverb, prepositional phrase, genitive). → `ArtSubs`
  - With a proper name. → `ArtProp`
  - With an abstract noun. → `ArtAbst`
  - A whole class. → `ArtGener`
  - Instead of "his / her" when the possessor is obvious. → `ArtPoss`
  - Otherwise. → `ArtPart`
- **αὐτός:**
  - After an article, meaning "the same". → `AutIden`
  - Nominative, or in predicate position with a noun, meaning "himself". → `AutEmph`
  - An oblique case standing alone, meaning "him, her, it". → `AutPron`
  - Referring to the subject, instead of ἑαυτοῦ. → `AutRefl`
