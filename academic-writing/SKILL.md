---
name: academic-writing
description: >
  Draft and revise research-paper prose, captions, tables, figures, and appendices for ML, AI, and adjacent technical venues. Use while writing or restructuring a regular conference or journal paper, improving argument flow, translating evidence into claims, or synchronizing prose with a changed visual. Use academic-self-check when a full review is requested or a substantial revision warrants one. For surveys use survey-writing, for outlines use academic-outline, and for reviewer responses use rebuttal-craft.
---

# Academic Writing

Write evidence-led research prose. Optimize for a reader who wants to understand the problem, the contribution, how the system works, what the experiments show, and where the evidence stops. Prefer a clear explanation over compressed terminology.

## Scope and judgment

Scale the workflow to the requested edit. For a local revision, use the established context, inspect the passage and its dependencies, and edit directly. Revisit the paper-wide argument only when it changes. The guidance below is a set of decision aids, not a mandatory sequence or a required response format.

Give secondary results space in proportion to their role. A baseline failure may need only a brief observation and interpretation in the main text, with diagnostic details in the appendix. Keep operational audit records out of the scientific narrative unless they change its interpretation. State material uncertainty where it matters without repeating the same caveat throughout the paper.

## Discovery-led empirical writing

For empirical method papers, write to show what the authors discovered. Do not organize every paragraph as a proof that the method is reasonable. Build interest through the scientific question, the comparison, the observed pattern, and what the pattern suggests. Use a curious, explanatory voice without manufactured suspense, promotional language, or a page full of rhetorical questions.

Prefer concrete findings such as "We find that the simpler rule performs better" over recurring claims such as "These results validate our design." Reserve "prove" and "guarantee" for actual formal results. Keep observations, tentative explanations, and causal findings distinct. This preference does not replace proof-oriented exposition in a theoretical paper or a genuine theorem section.

## ExRSI reference style

Use the author's supplied ExRSI/RSIAgent paper as a prose exemplar. For paragraph drafting or substantive prose revision, read [the ExRSI prose guide](references/exrsi-prose-guide.md), which distills its sentence connections, component explanations, and result narration with original transfer examples. Lead from a concrete situation, keep subjects and actions visible, and let each sentence carry a known object into the next step. Use direct statements as well as questions; discovery-led writing does not need repeated rhetorical openings. Adopt these explanatory habits selectively while preserving the manuscript's evidence and terminology.

## Main text for readers, appendix for audit

The author's working principle is: the main text is for human readers, and the appendix should also withstand AI-assisted review. Keep the main paper fluent and easy to follow, with clear ideas, familiar words, straightforward sentences, and ordinary punctuation. Avoid complicated sentence structures, stylistic dashes, semicolon chains, and repeated defensive qualifications. State the material boundary where the reader needs it, then continue the story.

Use the appendix for precise protocols, implementation edge cases, alternative interpretations, reproducibility details, and fuller limitations. It may be more technical and defensive when that resolves a concrete ambiguity. Keep it organized and evidence-based rather than adding speculative objections or boilerplate for its own sake. Keep details needed to interpret a headline result in the main text. Never hide a material limitation or invent an experiment, guarantee, configuration, or diagnostic to satisfy a reviewer.

Keep a detail when it helps readers understand the method, assess a central result, or reproduce a key experiment. The appendix need not preempt every hypothetical failure mode. Omit repeated disclaimers and speculation about unobserved problems. Preserve useful explanations grounded in observed behavior or cited prior results, including baseline diagnostics that clarify the comparison.

## Writing guidance

### 1. Establish the paper contract

For a new paper or substantial reframing, establish what is not already clear from the manuscript and conversation:

1. the paper's central problem and one-sentence answer;
2. the two to four contribution claims;
3. the evidence supporting each claim;
4. the intended venue, page limit, and anonymity mode;
5. the canonical terminology, notation, model names, and reported numbers.

Inspect adjacent sections and source artifacts before rewriting. If a requested claim is not supported, narrow it or mark the missing evidence. Do not silently invent experiments, reviews, data sources, implementation behavior, or release status.

### 2. Give each section one job

Use the section's purpose to decide what belongs there; no written planning artifact is needed for a local edit. Give every paragraph one primary function: establish a problem, explain a mechanism, report evidence, interpret a result, or connect two ideas. Merge paragraphs that merely restate one another. Split paragraphs that change purpose midway.

Consult [section-blueprints.md](references/section-blueprints.md) when a structural template would help with the abstract, introduction, method, experiments, related work, limitations, or conclusion.

### 3. Lead with meaning

State the idea before internal names and implementation detail. Introduce a component through what it does in the system, then name its interfaces. Avoid sentences that stack four or more nouns or responsibilities.

Prefer:

> The platform mediates the market. It checks an agent's request before the shared state changes.

Avoid:

> The runtime binds identity, references, replies, idempotency, validation, settlement, and governance.

When a process is easier to understand through an example, introduce one concrete actor goal and follow it through the mechanism. The example must be faithful to an implemented task or clearly labeled as illustrative.

### 4. Match claim strength to evidence

Use distinct language for distinct support:

| Support | Appropriate language |
| --- | --- |
| formal result | proves, guarantees, establishes under the stated assumptions |
| deterministic verification | verifies, reconstructs, passes the defined checks |
| measured result | observes, achieves, is associated with |
| qualitative inspection | suggests, is consistent with, may reflect |
| proposed use | can support, is designed for, provides an interface for |

Do not turn a capability into a demonstrated outcome. An interface for process rewards does not establish successful reinforcement learning. A multiagent environment does not by itself establish strategic multiagent evaluation. A public repository must not be described as available until it is actually accessible.

### 5. Present results as discoveries

Use the following questions to decide what the reader needs. Do not force each into a separate sentence or repeat setup already established:

1. the question;
2. the comparison or measurement;
3. the minimum numbers needed to support the conclusion;
4. the conclusion;
5. any boundary that materially changes the interpretation, stated once in the appropriate place.

Lead result paragraphs with the observed pattern and use the few numbers needed to make it concrete. Explain what is interesting about the finding. Avoid ending every paragraph with another assertion that the design is justified. Distinguish an interesting observation from a controlled causal finding.

### 6. Keep terminology and notation economical

Choose one term for each referent and one referent for each term. Define necessary acronyms once. Prefer a familiar phrase over a new compound term. Do not repeat acronym expansions already visible in an adjacent table.

Define every equation symbol at first use. Explain why the equation is present and what later reasoning depends on it. Remove an equation that only renames a prose list.

### 7. Apply the repository's prose conventions

In manuscript prose:

1. do not use em dashes or en dashes as stylistic punctuation;
2. do not use contractions;
3. avoid informal intensifiers and unsupported superlatives;
4. avoid unordered lists inside the paper unless the venue or content clearly requires one;
5. do not disguise a list as a sequence of bold inline labels in limitations or discussion;
6. keep each prose paragraph on one physical source line unless syntax requires a break;
7. prefer declarative, concrete subsection titles over abstract noun stacks or a page full of questions;
8. avoid one-sentence paragraphs unless the sentence has a deliberate structural role.

Treat 35 words as a warning threshold, not a mechanical limit. Split a long sentence when it carries more than one logical relationship.

Load [writing-examples.md](references/writing-examples.md) when a passage feels dense, repetitive, abstract, or disconnected from its figure.

## Figures and Tables

Choose the representation by the claim:

| Intended reading | Preferred form |
| --- | --- |
| exact lookup | table |
| trend or comparison | chart |
| process or responsibility | diagram |
| concrete task structure | compact example box |

If information density is high, reduce decorative color. If information density is low, color may establish grouping or emphasis. Never use color to compensate for weak hierarchy.

Write a visual so it can be read at final paper size. Keep labels human-readable, align repeated elements, use one arrow grammar, and remove internal titles that duplicate the caption. A caption should state what is shown and the takeaway needed to interpret it. The nearby prose should explain the implication rather than restate every element.

Load [figure-table-review.md](references/figure-table-review.md) whenever creating or substantially revising a visual.

## Revision Workflows

### Framing change

When the paper's emphasis changes, update the title, abstract, introduction, contribution list, section openings, figure captions, results interpretation, limitations, and conclusion. Search for residual language from the old framing.

### Data or model-panel change

Trace a changed result to affected aggregates, claims, tables, and plots, and update those dependencies together. Recompute what depends on the change; broaden the audit only when inconsistencies or a wider revision justify it.

### Figure change

After changing a figure, inspect every reference to its number, panels, visual encoding, and takeaway. Remove descriptions of deleted content. Keep the figure near its first substantive discussion.

### Moving material

After moving content between the main paper and appendix, repair transitions, references, numbering, and claims of self-containment. Do not leave an orphan appendix artifact or a main-text promise whose evidence moved away.

## Finish the Draft

Compile or render the paper after substantive edits. Inspect the relevant pages, not only the log. Fix obvious overflow, overlap, stranded headings, one-word terminal lines, large unexplained whitespace, and figures separated from their analysis.

Check the changed passage and its dependencies. Use `academic-self-check` for a requested full review, a substantial revision, or a concrete unresolved concern. A local edit does not require a full-paper audit or a separate agent.
