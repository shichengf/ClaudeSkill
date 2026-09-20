---
name: academic-writing
description: Draft and revise empirical ML and AI papers, including titles, abstracts, section structure, evidence narration, and experiment planning when requested. Use for readable discovery-led research prose and manuscript revisions; preserve formal proof exposition in theoretical work.
---

# Empirical Research Writing

Write a paper that lets a reader understand a problem, follow an idea, and learn from the evidence. The author's reference corpus comprises Planner Matters, CD-LAM, StructAgent, and RSIAgent. Learn their explanatory habits and choice of comparisons, not their wording, scientific claims, or domain-specific vocabulary.

## Start with the requested job

For a local edit, read the passage and its immediate dependencies, then edit it. For a substantial rewrite, identify the central finding, mechanism, and evidence already available. For experiment planning, distinguish an untested proposal from a completed result. A writing task does not authorize new training, benchmark collection, or a mandatory paper-wide audit.

Use these references as needed:

- [Section blueprints](references/section-blueprints.md): title, abstract, introduction, preliminaries, method, results, discussion, related work, conclusion, and appendix.
- [Prose and examples](references/writing-examples.md): sentence connections, useful verbs, terminology, paragraph rhythm, and original transfer examples.
- [Experiment design and narration](references/experiment-design.md): choose comparisons that answer the paper's questions and organize existing evidence around them.
- [Figures, tables, and layout](references/figure-table-review.md): align visuals with claims and inspect the rendered manuscript, including paragraph endings.
- [Reference corpus](references/reference-corpus.md): where the patterns occur, how the four papers differ, and what should not be generalized.

For a full rewrite, read the first three references and inspect the current figures and result tables. Read the corpus notes when adapting a reference-specific pattern. The guides are self-contained; unavailable source PDFs do not block later writing.

## Build the paper around a discovery

Find a concrete tension that the experiments resolve. A model may produce plausible outputs while missing the requested behavior. A component may matter much more than another. A simple signal may be useful despite incomplete coverage. State the actual tension in this paper rather than borrowing one from the references.

Let the narrative follow what the work teaches: observed difficulty, idea, mechanism, comparison, finding, implication. This is a reasoning order, not a required six-part outline. A diagnostic may precede the method when it motivates the design; a benchmark result may precede analysis when the design is already easy to understand.

Write to reveal findings rather than repeatedly justify the design. Report what changed and what that comparison tells the reader. Avoid recurring conclusions such as "validates the effectiveness and necessity of our framework." Reserve proof language for formal results. Discovery-led prose may be direct and declarative; it does not require rhetorical questions or manufactured suspense.

## Make the contribution worth caring about

Use ambitious, evidence-backed framing. Connect the work to a major research question when the mechanism and experiments make that connection concrete. Preserve a memorable title, a sharp problem statement, and a clear account of why the contribution matters. Discovery-led writing should create interest as well as readability; it must not reduce the paper to an implementation summary.

Distinguish unsupported claims from strong presentation. Remove the unsupported mechanism or narrow the claim to its actual operation, rather than weakening the entire story. Prefer a precise, confident claim such as "replaces per-sentence neural verification in the RL reward loop" over either an unbounded replacement claim or a timid description of "using counts as a simple reward." State supported gains directly. Keep material qualifications where readers need them, without preemptively repeating limitations in the title, abstract, and every introduction paragraph.

Respect the author's preferred positioning and title. A broad topic, memorable contrast, or compelling headline is welcome when the paper explains the connection. Do not remove it merely to sound cautious. For CorVer, retain Beyond Math and Code, the reward-cost bottleneck, and corpus-grounded process supervision. Keep full-run timing distinct from isolated verifier timing, and do not invent shared neural-verifier/policy blind spots or circularity as an established motivation.

## Make mechanisms easy to follow

Introduce a component through its purpose, then explain the information it receives, the operation it performs, and where its output goes. Keep a concrete object moving through successive sentences: a task becomes a subgoal, an observation becomes evidence, or a corpus count becomes a local reward.

Use stable nouns and active verbs. Prefer "the index returns a count" to an abstract phrase about count acquisition. Repeat an important noun when it makes the connection clearer. Split a sentence when it asks the reader to follow several logical relationships, not merely because it exceeds an arbitrary word count.

Name the few distinctions that organize the paper. Introduce notation at the operation it describes, keep symbols stable, and interpret consequential equations in ordinary language. Do not turn empirical intuition into a theorem or add equations merely to rename prose.

## Let the evidence determine the claim

Separate the behavior observed, the explanation proposed, and the intervention actually tested. An ablation supports the tested comparison; it does not establish universal necessity. A metric diagnostic may clarify why rankings differ without invalidating an entire benchmark. A configuration-level time comparison is not automatically an isolated component speedup.

Keep central comparisons recognizable: the model, data, metric, training or inference stage, and the variable being changed. Distinguish matched comparisons from published reference scores and fresh task-specific training from transfer without retraining. State a material qualification once where it changes interpretation, rather than repeating it throughout the paper.

Preserve numerical results, formulas, actual procedures, sample sizes, citations, and established terminology during a prose edit. Do not invent experiments, seeds, metrics, prompts, released artifacts, or causal evidence. Do not imply that a sample audit is a full-dataset evaluation. Preserve a meaningful exception even if a smoother sentence could conceal it.

## Give the main text and appendix different jobs

The main text carries the argument and the evidence needed to understand it. Use the appendix for exact settings, complete results, reproducible scoring rules, and a small number of informative diagnostics or cases. The appendix should withstand close reading, including AI-assisted review, without becoming a catalogue of imagined objections.

Keep details that explain the method, change interpretation of a central result, or enable reproduction. Put operational history, debugging chronology, and internal audit records outside the scientific narrative unless scientifically relevant. A failed baseline can deserve a concise observed explanation, not a competing story. Do not remove a substantive limitation just to sound confident.

## Finish at the paper's actual size

Preserve the author's tone: familiar words, straightforward syntax, ordinary punctuation, no contractions, and no stylistic dash or semicolon chains. Prefer concrete declarative headings. Parallel lists are available when useful; neither contribution bullets nor question headings are mandatory. Keep each prose paragraph on one physical LaTeX source line where practical.

After substantive LaTeX edits, compile, check references and overflow, and view affected pages. In this author's main text, a paragraph's final line should normally occupy at least one third of its actual column width, preferably more than half. Eliminate one- or two-word endings by natural compression or information the reader needs. Do not pad prose, distort spacing, shrink the font, or alter scientific meaning to hit a line-width target. Respect an instruction to leave appendix layout alone.

Review revised passages together with their captions and claim-bearing data. Report what changed, what was checked, and any actual unresolved issue. Do not manufacture follow-up experiments from a style review. Keep privately supplied reference PDFs local and outside version control unless the author explicitly asks otherwise.
