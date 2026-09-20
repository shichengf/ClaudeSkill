# Prose and original transfer examples

These examples are newly written. They illustrate habits found across the reference corpus and are not quotations to reuse indiscriminately.

## Connect sentences through the thing being explained

Keep one object visible as it changes or moves. Introduce it, describe an operation on it, then describe the resulting information or behavior.

Dense: "The corpus-based entity-pair reward construction pipeline facilitates localized policy optimization."

Clear: "The extractor identifies an entity pair in each sentence. We query its co-occurrence in Wikipedia and convert the count into a sentence reward. Tokens in that sentence receive the local feedback during training."

This is the move used when the agent papers carry a subgoal through execution and verification, or when CD-LAM carries a representation through successive training stages. The scientific procedure must come from the current manuscript.

## Use concrete subjects and verbs

Useful verbs describe work: receives, stores, extracts, selects, compares, returns, updates, removes, retains, rises, falls, improves. A model, component, input, or measurement is often a better subject than "the implementation," "the effectiveness," or "the utilization."

Dense: "The implementation of an outcome-grounded consolidation procedure enables the enhancement of reusable knowledge."

Clear: "After verification, the actor updates memory with the experience that later tasks can reuse."

Do not merely replace a technical term with a longer phrase. Keep terms that name the actual scientific distinction, and explain them at first use.

## Give a component a purpose before its machinery

Start with the question making the component useful, then explain how it works. A result can also make the purpose apparent without an explicit "to address" sentence.

Example: "A response-level score treats every sentence alike. CorVer adds a local reward so that sentences within the same response can receive different feedback."

Next describe the actual mapping and normalization. Do not introduce every symbol and hyperparameter before readers know what is being computed.

## Make transitions carry an argument

Use transitions to mark a relationship, not decorate every paragraph.

- "We next examine ..." changes the experimental question.
- "The same ..." carries an established signal or mechanism into a new use.
- "This suggests ..." introduces an interpretation of the preceding observation.
- "In these runs ..." bounds an empirical statement when the boundary matters.
- "After ..." locates an operation in the actual procedure.

Avoid beginning every paragraph with "Building on this," "Importantly," or "Furthermore." Prefer a concrete link: "The retained pair defines the query" or "A3 keeps the signal but changes where it is assigned."

## Keep rhythm without making prose choppy

Mix explanatory sentences with shorter statements naming a contrast or result. Use longer sentences when their clauses express one clear relationship. Split when a sentence changes subject repeatedly, nests conditions, or hides the main action behind a long parenthesis.

Dense: "From the extracted triplets, we retain the first valid one (nonempty, non-pronominal entities forming a query with at least two distinct content terms), discarding the relation since only the pair is used."

Clear: "We retain the first valid triplet and use its head and tail as the entity pair. A valid pair has nonempty, non-pronominal entities whose content words form a query with at least two distinct terms. The relation is not included in the query."

This preserves the rule. Whether the extra sentence helps depends on paragraph density and available space.

## Explain a finding without proving the design

Defensive: "These ablations validate the effectiveness and necessity of our proposed token-level alignment."

Empirical: "A3 keeps the corpus signal but assigns it as one response score. Accuracy falls on all five benchmarks, suggesting that local assignment contributes alongside the signal itself."

The comparison supplies the evidence. Avoid universal necessity for an empirical ablation. Equally, avoid weakening every measured fact with "may possibly": report the observation directly, then calibrate its explanation.

## Tell the reader what differs across conditions

Inventory: "A1 decreases accuracy. A2 decreases accuracy. A3 decreases accuracy."

Connected: "Both reward sources contribute, but their effects differ across datasets. Removing answer-level supervision produces the largest drop on some benchmarks, while removing corpus feedback costs more on others. Averaging the corpus signal into one response score also reduces accuracy."

Use the exact datasets and numbers when they matter. Do not replace a necessary comparison with vague praise.

## Make qualifications local

Heavy: "This result is only a point estimate, not a proof, and cannot establish that the method is universally superior."

Proportionate: "CorVer and FSPO are close on this model, with a 0.05-point difference in macro accuracy."

Keep the single-run protocol in setup if that is the actual procedure. Repeated uncertainty language obscures the observation without adding evidence. A materially incomparable baseline still needs an explicit condition.

## Make limitations concrete

Vague: "The method is subject to inherent limitations and cannot guarantee complete factual correctness."

Concrete: "A frequent entity pair can occur with an incorrect relation. Co-occurrence therefore leaves some false claims unpenalized."

A useful case traces the error from input through the method to the outcome. Preserve authentic generated text; polish only the surrounding explanation.

## Edit terminal lines without changing the science

Measure a main-text paragraph's last line against its actual column width, including wrapfig and minipage layouts. Aim for more than half a line; normally keep at least one third. A heading, equation, table cell, or quoted output is not a prose paragraph ending.

Remove an unnecessary modifier or restructure a sentence to eliminate a one-word tail. If a useful explanation is missing, add a precise consequence already supported by the method or results. Do not invent a claim, remove a meaningful qualification, or add reassurance just to fill space. Recompile because a local change can create a new tail in a wrapped paragraph.

## Preserve excitement while correcting the scope

Too flat: "We use Wikipedia counts as a simple reward."

Stronger and specific: "CorVer replaces per-sentence neural verification in the RL reward loop with a lightweight corpus-indexed signal."

The second sentence identifies a meaningful operation and its alternative. A small extractor can still identify entities; the replacement claim concerns verification in the reward loop. Introduce the reward-cost bottleneck and the connection to process supervision beyond math and code, then give the measured accuracy and complete-run timing results. Do not turn that timing into an isolated verifier speedup or invent an untested neural-verifier failure mechanism.

Readable writing and persuasive positioning work together. Retain a supported headline and compelling research story instead of replacing every strong sentence with a caveat.
