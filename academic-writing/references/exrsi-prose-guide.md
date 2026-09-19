# ExRSI prose reference

Use this guide when drafting or revising empirical paper prose in the author's preferred style. It distills the supplied `ExRSI.pdf`, titled *RSIAgent: Autonomous Exploration for Recursive Self-improvement in New Environments*. Page references below use the PDF page numbers. They identify the writing examples, not independent verification of that paper's scientific claims. The guidance is self-contained; the original PDF is not required for later use.

## What makes the prose easy to follow

### Start from a situation the reader can picture

In the abstract and introduction (pp. 1–2), the paper starts with agents encountering unfamiliar software, explains why existing adaptation is costly, and then introduces autonomous exploration. The problem gives the method a reason to exist before the component names arrive.

For a new abstract, a useful opening is the concrete task and its difficulty, followed by what the paper explores. A direct statement often works better than a rhetorical question. In an introduction, let the unresolved question emerge from the preceding observation. Discovery-led writing does not require opening every section with a question.

### Keep the actors and their actions visible

Section 3.2 (p. 5) explains each agent through its responsibility, the information it uses, and the output that feeds the workflow. The reader can follow who proposes, executes, checks, and updates. Technical terms attach to operations that are already understandable.

In another paper, use the actual subjects: the extractor identifies a pair, the index returns a count, the reward assigns feedback, or the policy generates an answer. Prefer these verbs to noun-heavy phrases such as "the implementation of the assignment mechanism." Explain a component's purpose before its internal name or notation when the ordering is flexible.

### Carry one object through successive sentences

The actor description (p. 5) introduces memory, explains how it changes after verification, and then describes how later actors reuse it. The same object links the paragraph. Section 3.3 (pp. 5–6) similarly carries tasks into execution, outcomes into feedback, and feedback into the next exploration step.

Use this continuity in a method paragraph: extracted pair → query → count → reward → token feedback. Each sentence should inherit something the reader already understands and add the next operation. It is fine to repeat the canonical noun when that avoids ambiguity. Do not rotate through synonyms merely to sound varied.

### Use sentence length to separate logical steps

The sample mixes explanatory sentences with short statements that mark a transition, such as freezing memory before evaluation (pp. 5–6). Its clarity does not come from making every sentence short.

Split when a sentence asks the reader to track several operations, an exception, and a cross-reference at once. Move a long parenthetical condition into an ordinary sentence. Retain subordinate clauses when they express one useful relationship. Avoid replacing fluent prose with clipped fragments, a rigid word limit, or a repeated five-sentence template.

### Introduce stages by their different jobs

The broad/deep exploration descriptions (pp. 5–6) first explain coverage and refinement, then show how each loop achieves its purpose. Similar components receive parallel descriptions, so their difference is easy to see.

For CorVer, distinguish corpus feedback, final-answer supervision, and local assignment by what information each supplies or where it acts. Describe the actual procedure before arguing for its value. Keep notation, equations, and necessary validity conditions precise; a clear prose style does not justify deleting method-defining details.

### Turn result lists into observations

Section 4.4 (pp. 8–9) moves from the stage comparison to the aggregate pattern and then the exceptions. Section 4.5 (p. 9) organizes results by what happens for different starting game qualities instead of reciting every table cell. Section 4.3 (p. 8) connects score jumps to the evolving memory, giving the reader an interpretation of the curve.

Choose the observation that makes the comparison interesting. Use only the numbers needed to see it, then explain its implication. Group ablations by the scientific distinction they expose, rather than merely narrating row A1, then A2, then A3. Interpretations must remain proportional to the evidence: a plausible explanation is not a measured causal mechanism.

### Explain limitations through observed behavior

Section 4.6 (pp. 9–11) describes concrete failures and how they propagate: a missing requirement escapes checking, an accepted decision enters memory, and later attempts reuse it. This makes the limitation understandable without a catalogue of imagined objections.

When a limitation matters, name the failure and its consequence. Put implementation boundaries or detailed diagnostics next to the evidence that needs them. Do not end every result paragraph with a caveat or an assertion that the design has been validated.

## Original transfer examples

These examples apply the observed techniques to CorVer. They are newly written examples, not quotations from ExRSI and not authority for changing the manuscript's scientific content.

**Dense mechanism**

Before: "The reward pipeline consists of entity-pair extraction, content-word reduction, and word-level AND query submission for sentence-level co-occurrence reward construction."

After: "CorVer scores each sentence using a subject–object pair. It reduces the entities to content words and queries their co-occurrence in Wikipedia. The resulting count determines the sentence reward."

Why: A reader can follow the same pair through successive operations. In a real revision, keep the exact pair-selection and query semantics in the surrounding passage.

**Defensive result interpretation**

Before: "The A3 ablation validates the effectiveness and necessity of our token-level alignment design."

After: "A3 retains the corpus signal but assigns it as a single response score. Accuracy falls on all five benchmarks, suggesting that where the feedback is assigned matters alongside the feedback itself."

Why: The comparison and observation carry the argument. The prose does not claim universal necessity.

**Disconnected experimental transition**

Before: "Complementing the preceding analyses, we further comprehensively investigate cross-dataset applicability."

After: "We next examine whether corpus feedback also helps on questions that require multiple reasoning steps."

Why: The transition introduces the next scientific question in familiar language. State target-task training explicitly in the subsequent setup if that is how the experiment was performed.

## Apply selectively

Adopt the sample's explanatory sequence and sentence connections. Do not import its agent-specific terminology, scientific claims, repeated intensifiers, or every formatting choice. The author's existing preference for ordinary punctuation and discovery-led empirical claims remains in force. No mandatory human-learning analogy, contribution list, or fixed set of transition words is required.

During revision, identify what the paragraph lets the reader understand, follow the concrete objects through it, and remove wording that interrupts this progression without adding necessary meaning. Preserve data, formulas, citation provenance, and material experimental conditions. Aim for similar paragraph length when layout matters, but do not pad prose to preserve an exact word count. Compile and inspect affected pages after substantive LaTeX edits.
