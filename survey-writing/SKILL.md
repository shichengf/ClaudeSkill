---
name: survey-writing
description: >
  Write survey (review) papers in ML/AI: generate publication-ready academic prose for any
  section of a short survey (10-15 pages, TMLR, ACM Computing Surveys, Foundations and
  Trends). Trigger whenever the user asks to write, draft, or revise survey sections:
  introduction, background, taxonomy, thematic literature analysis, comparative discussion,
  open problems, future directions, or conclusion. Also trigger for taxonomy design,
  organizing papers thematically, writing subfield-spanning related work, or critically
  analyzing a body of literature. Handles both full-survey writing and individual sections
  for collaborative writing. Trigger on "review paper", "literature review", "position
  paper", "SoK", or "综述". Do NOT use for regular conference paper sections (use
  academic-writing) or outlines without prose (use academic-outline).
---

# Survey Writing Skill

This skill governs all survey (review) paper writing. A survey is not a paper list. It is
a structured argument that synthesizes a field, reveals patterns invisible in individual
papers, and charts a principled path forward. Every paragraph Claude produces under this
skill must meet the standards of a top-tier venue survey submission.

Core philosophy: **synthesis over summary, taxonomy over listing, argument over
description, and honest assessment over diplomatic hedging.**

---

## 0. Preamble: What Makes a Survey Valuable

A survey paper serves the scientific community. Its value comes from three things that no
individual paper provides: (1) a principled organizational framework (taxonomy) that
reveals structure in a fragmented literature, (2) cross-method analysis that identifies
shared assumptions, recurring failure modes, and underexplored combinations, and (3)
concrete, actionable research directions grounded in the gaps the taxonomy exposes.

A survey that merely describes each paper in sequence ("X did A, Y did B, Z did C") adds
no value beyond a bibliography. The reader could have found those papers themselves. The
survey must tell the reader something they could not easily learn by reading the original
papers independently.

---

## 1. Foundational Rules

### 1.1 No Dashes

Never use em dashes, en dashes, or any dash-like punctuation as a stylistic device. This
rule is absolute and applies to all output.

(a) Em dash as parenthetical: "The method, which we call X, achieves..." not "The
method --- which we call X --- achieves..."

(b) En dash as range: Write "from 5 to 10" in prose. The en dash is acceptable only
inside tables or parenthetical numerical ranges in LaTeX.

(c) Dash as informal connector: Never appropriate in academic writing.

### 1.2 No Unordered Lists

Never use bullet points or unordered lists. Academic surveys flow in complete paragraphs
and sentences. When enumerating, use ordered structures: (1), (2), (3) or (a), (b), (c).

### 1.3 Synthesis, Not Summary

Every paragraph must do more than describe what a paper did. It must place that work in
relation to other work, identify what it shares with or differs from neighboring
approaches, and connect it to the taxonomy. The test: if you can delete a paragraph and
replace it with a citation without losing argumentative content, the paragraph was a
summary, not a synthesis.

### 1.4 No Paper-by-Paper Structure

Never organize a section by giving each paper its own paragraph or subsubsection. Instead,
organize by conceptual theme, methodological principle, or taxonomic dimension. Individual
papers appear as evidence within thematic arguments, not as standalone entries.

### 1.5 Every Section Earns Its Place

Before writing any section, ask: what does the reader learn from this section that they
could not learn from any other section? If two sections teach the same lesson, merge them.
If a section teaches nothing beyond what its cited papers already say, it is a list
disguised as prose.

### 1.6 Consistent Terminology

Map terminological variations across the literature explicitly. Different communities may
use different terms for the same concept (e.g., "domain shift" vs. "distribution shift"
vs. "dataset bias"). A survey must establish a canonical term on first occurrence, note the
variants, and use the canonical term consistently thereafter.

### 1.7 No Citation Dump Tails

Never end a paragraph with a sentence that lists additional works without synthesis. Common
offending patterns include:

(a) "Additional works extend this to X~\citep{A}, Y~\citep{B}, and Z~\citep{C}."
(b) "Further efforts include~\citep{A, B, C, D}."
(c) "The same paradigm has been applied to X, Y, Z, and W~\citep{...}."

Pattern (c) is especially insidious because it disguises the dump with a thematic opening
phrase while retaining the same enumeration structure. The test: if the sentence lists more
than two domain applications separated by commas with per-item or grouped citations, it is
a dump regardless of its opening phrase. Fix by either (1) merging citations into a nearby
\citep{} call that already supports the claim, (2) compressing to a single short sentence
under 20 words with all citations grouped and no per-item enumeration, or (3) deleting
entirely if the works are tangential.

### 1.8 No Intro-Closing Redundancy

Within a subsubsection or paragraph group, the intro and closing must not restate the same
claim. A common failure: the intro defines a method family and names its key advantage,
then the closing repeats the advantage in different words. The fix: the intro defines what
the family is and previews internal structure; the closing states limitations, open
problems, or connections to adjacent sections. They serve different rhetorical functions
and must contain different content. If you find yourself writing a closing that echoes the
intro, delete the closing's first sentence and start directly with the limitation.

### 1.9 Proportional Shell-to-Body Ratio

When a subsubsection has intro and closing paragraphs wrapping body \paragraph{} entries,
the shell (intro + closing) should not exceed 40% of total word count. If it does, either
the body is too thin (add substance) or the shell is too thick (compress). A single-body
subsubsection (only one \paragraph{}) almost always signals that either (a) the intro
should be folded into the body, or (b) the body should be split into two \paragraph{}
headings to justify the shell's existence.

### 1.10 Demote Low-Distinction Papers

Not every cited paper deserves a standalone sentence. Before giving a paper its own
description, ask: does this paper's contribution differ from its neighbors in a way the
reader needs to understand? If the answer is no (e.g., it is "an open-source platform"
for the same paradigm, or it automates the same pipeline with a different implementation),
demote it to a grouped citation attached to a neighbor. The "expand two, group the rest"
pattern (Section 3.4) operationalizes this: expand the two most representative methods,
then group remaining methods in merged \citep{} calls.

---

## 2. Survey Architecture

A short survey (10 to 15 pages) typically follows this macro structure. Section lengths are
approximate and should be adjusted based on the field's maturity and the paper's emphasis.

### 2.1 Macro Structure

(1) **Introduction** (~1.5 pages): Motivation, scope, positioning relative to existing
surveys, contributions, and a roadmap paragraph.

(2) **Background / Preliminaries** (~1 to 1.5 pages): Formal definitions, notation, and
foundational concepts that a reader needs before encountering the taxonomy. This section
is not a mini-textbook; include only what is necessary for the survey's arguments.

(3) **Taxonomy / Framework** (~0.5 to 1 page): The organizational principle. Present the
taxonomy as a figure or table, then justify each axis. This section may be folded into
the introduction if the taxonomy is simple, or may be a standalone section if the taxonomy
requires formal justification.

(4) **Main Body** (~5 to 7 pages): Organized by taxonomy dimensions, not by paper. Each
subsection corresponds to a branch of the taxonomy. Within each subsection, synthesize
the literature thematically.

(5) **Comparative Analysis / Discussion** (~1 to 1.5 pages): Cross-cutting observations
that span multiple taxonomy branches. Identify shared assumptions, recurring limitations,
underexplored combinations, and empirical trends (e.g., "methods in Branch A consistently
outperform Branch B on metric X, but require 10x more data").

(6) **Open Problems and Future Directions** (~1 to 1.5 pages): Concrete, actionable
research directions. Each direction should be grounded in a specific gap identified in
the main body or discussion.

(7) **Conclusion** (~0.5 page): Summary of key findings and the survey's main message.

### 2.2 Section Dependencies

When writing a single section in isolation (collaborative writing), Claude must ask the
user for context about:

(a) The taxonomy structure (what are the axes and branches?).
(b) The scope of the survey (what is in and out of scope?).
(c) Notation and terminology conventions already established.
(d) What other sections exist and what they cover (to avoid redundancy).

If this context is unavailable, Claude should state its assumptions explicitly and flag
them for the user to verify.

---

## 3. Section-Level Blueprints

### 3.1 Introduction

The introduction of a survey differs from that of a research paper. It must accomplish
six things:

**P1: The Field and Its Significance** (~3 to 4 sentences)
  S1 to S2: Establish the broader field and why it matters.
  S3 to S4: Narrow to the specific subfield the survey covers.

**P2: Why a Survey Is Needed Now** (~3 to 4 sentences)
  S1: State the volume or velocity of recent work (e.g., "Over 200 papers on X have
  appeared since 2022").
  S2 to S3: Identify the fragmentation problem: multiple communities, inconsistent
  terminology, or conflicting empirical claims that make the landscape hard to navigate.
  S4: State the consequence: practitioners and newcomers cannot easily identify the
  state of the art or the most promising directions.

**P3: Existing Surveys and Their Gaps** (~3 to 5 sentences)
  S1 to S2: Acknowledge prior surveys with citations. Be specific about what each
  covers.
  S3 to S4: Identify what they miss. Avoid vague claims like "they do not cover recent
  work." Instead, name the specific topics, methods, or perspectives that are absent.
  S5: State how the present survey fills these gaps.

**P4: Scope and Taxonomy Preview** (~3 to 4 sentences)
  S1: Define the scope explicitly (what is included, what is excluded, and why).
  S2 to S3: Preview the taxonomy at a high level. The reader should understand the
  organizational principle before encountering the details.
  S4: Mention the number of papers surveyed and the time range covered, if relevant.

**P5: Contributions** (~3 to 5 sentences, ordered list)
  Use "(1) We provide..., (2) We propose..., (3) We identify..." format. Each
  contribution must be concrete. Good: "(1) We propose a two-dimensional taxonomy
  organizing 150 methods along the axes of supervision signal and temporal granularity."
  Bad: "(1) We provide a comprehensive survey of the field."

**P6: Roadmap** (~2 to 3 sentences)
  "The remainder of this paper is organized as follows. Section 2 introduces..."
  Keep this mechanical and short. Do not re-describe the contributions.

### 3.2 Background / Preliminaries

This section provides the minimum formal machinery the reader needs. It is not a textbook
chapter.

**What to include:**
(a) Formal definitions of the core problem or task.
(b) Notation table or notation paragraph defining all symbols used throughout the survey.
(c) Foundational concepts that most surveyed papers build on (e.g., for a CRL survey:
structural causal models, identifiability, ICA).

**What to exclude:**
(a) Material that any reader in the target venue would already know.
(b) Lengthy derivations or proofs (cite the original source instead).
(c) Background on individual surveyed methods (that belongs in the main body).

**Structure pattern:**
Each concept gets one paragraph. The paragraph follows: definition (1 to 2 sentences),
intuition or significance (1 to 2 sentences), and connection to the survey's scope (1
sentence). Example:

  "A structural causal model (SCM) is a tuple $(V, U, F, P(U))$ where $V$ denotes
  observed variables, $U$ exogenous noise, $F$ a set of functional assignments, and
  $P(U)$ the noise distribution~\citep{Pearl2009}. SCMs encode both the observational
  distribution and the effect of interventions, making them the standard formalism for
  causal reasoning. In this survey, we use SCMs as the common language to compare methods
  that otherwise adopt heterogeneous notations."

### 3.3 Taxonomy Design

The taxonomy is the survey's primary intellectual contribution. It must satisfy three
properties:

**(a) Principled axes.** Each axis of the taxonomy must correspond to a fundamental
design choice, assumption, or problem dimension, not an arbitrary grouping. Good axis:
"type of supervision signal (labels, interventions, temporal structure, counterfactuals)."
Bad axis: "year of publication" or "first author's institution."

**(b) Exhaustive coverage.** Every surveyed paper must fit into exactly one cell of the
taxonomy. If a paper does not fit, either the taxonomy is incomplete or the paper is out
of scope. Papers that span multiple cells should be noted explicitly.

**(c) Discriminative power.** The taxonomy must distinguish methods that differ in
meaningful ways. If two methods that solve fundamentally different problems end up in the
same cell, the taxonomy lacks resolution. If two nearly identical methods end up in
different cells, the taxonomy over-discriminates.

**How to present the taxonomy:**

(1) A figure (tree diagram, matrix, or Venn diagram) that shows the full structure at a
glance. This figure is often the most-referenced element of the survey.

(2) A paragraph for each axis explaining: what the axis captures, why it matters (what
practical or theoretical consequences follow from the choice), and what values the axis
takes.

(3) A summary table mapping representative papers to taxonomy cells. This table serves as
a quick-reference index for the reader.

**Common taxonomy pitfalls to avoid:**

(a) Retrofitted taxonomy: designing the taxonomy after writing the main body, so that the
taxonomy merely reflects the section structure rather than driving it. The taxonomy should
come first and dictate the organization.

(b) Single-axis taxonomy: using only one dimension (e.g., "method type") when the
literature varies along multiple independent dimensions. Consider whether a second axis
(e.g., "assumption strength" or "evaluation setting") would add discriminative power.

(c) Overlapping categories: if a large fraction of papers belong to multiple categories,
the categories are not well-defined. Refine the axis definitions or add a "hybrid"
category with explicit criteria for membership.

(d) Taxonomy by implementation detail: grouping by "uses transformers" vs. "uses RNNs"
rather than by the conceptual approach. Implementation choices change rapidly; conceptual
distinctions are more durable.

### 3.4 Main Body Sections

Each main body section corresponds to one branch (or one level) of the taxonomy. The
internal structure of each section follows a consistent pattern:

**Opening paragraph: Branch Overview** (~3 to 4 sentences)
  S1: Define the branch and state what unifies the methods in it.
  S2: State why this approach is natural or appealing (what problem does it solve
  elegantly?).
  S3 to S4: Preview the internal structure of the section (e.g., "We further distinguish
  methods that use paired observations from those that rely on unpaired data").

**Middle paragraphs: Thematic Synthesis** (variable length)
  Each paragraph covers one sub-theme, not one paper. The paragraph follows the
  "claim, evidence, assessment" pattern:

  (a) Claim sentence: "A common strategy for handling unobserved confounders is to
  impose sparsity constraints on the latent space."

  (b) Evidence sentences (2 to 4): Describe 2 to 4 methods that instantiate this
  strategy, emphasizing what they share and how they differ. Use the "expand two, group
  the rest" pattern from academic writing: expand the two most representative methods
  (1 to 2 sentences each), then group remaining methods in a single sentence with merged
  citations.

  (c) Assessment sentence: State the collective strength or limitation of this group of
  methods. "While effective for low-dimensional latents, sparsity-based approaches
  struggle when the true latent dimensionality is unknown."

**Closing paragraph: Branch Summary** (~2 to 3 sentences)
  S1: Summarize the key insight from this branch.
  S2: Identify the most important open question specific to this branch.
  S3: Optionally, preview the connection to the next section.

**Key writing patterns for the main body:**

(a) **Comparative sentences over descriptive sentences.** Bad: "Method A uses a VAE.
Method B uses a flow model." Good: "While A and B both target the same identifiability
guarantee, they differ in the generative model: A uses a VAE whose posterior may be
misspecified, whereas B uses a normalizing flow that provides exact likelihoods at the
cost of architectural constraints."

(b) **Temporal evolution when relevant.** If the sub-theme has a clear developmental arc
(early heuristic approaches replaced by principled ones), narrate this arc. But do not
default to chronological ordering when thematic ordering is more informative.

(c) **Tables for dense comparisons.** When comparing more than 4 methods along more than
3 dimensions, use a comparison table rather than prose. The table should appear near the
relevant text, and the prose should highlight the most interesting patterns in the table
rather than restating every cell.

(d) **Sentence variety.** Never use the same "Method X does Y; however, Z" template for
consecutive citations. Alternate between concessive clauses ("While X achieves..."),
contrast ("Unlike X, Y takes..."), concession ("Although X demonstrates..., it
relies on..."), and group summaries ("A, B, and C all produce...; none, however,
can...").

### 3.5 Comparative Analysis / Discussion

This section is what separates a good survey from a mediocre one. It contains observations
that require reading the entire literature, not just individual papers.

**What to include:**

(a) **Cross-branch patterns.** "Methods in Branch A assume access to interventional data
while methods in Branch B operate from observational data alone. Interestingly, no method
combines both data types, despite the natural availability of mixed data in
clinical settings."

(b) **Shared assumptions and their consequences.** "Of the 45 methods surveyed, 38
assume i.i.d. data. For time-series applications, this assumption is untenable, yet only
7 methods address temporal dependencies."

(c) **Empirical landscape analysis.** "Benchmark X is used by 30 of 45 methods, but
its ground truth contains systematic biases (noted by~\citet{...}). Results on
Benchmark Y, which has fewer known issues, show a different ranking of methods."

(d) **Scalability and practicality.** "Most methods are validated on latent spaces of
dimension 5 to 20. Scaling to dimensions above 100 remains untested."

(e) **Summary comparison table.** A comprehensive table comparing all major methods
across key dimensions: input requirements, assumptions, theoretical guarantees,
computational cost, and empirical benchmarks used. This table is often the most useful
artifact in the survey for practitioners.

**What to avoid:**

(a) Repeating the main body in compressed form.
(b) Vague observations without evidence ("there is much room for improvement").
(c) Taking sides without justification. If the survey argues that one approach is
superior, it must provide concrete evidence.

### 3.6 Open Problems and Future Directions

This section is the survey's forward-looking contribution. Each direction must be concrete
and actionable. The pattern for each direction is:

**Structure per direction** (~1 paragraph each, 4 to 8 directions total):

  S1: Name the direction concisely (this serves as an implicit heading).
  S2 to S3: State the gap. What is missing from the current literature, and why does it
  matter? Ground this in specific evidence from the survey (e.g., "As shown in Table 3,
  no method achieves both identifiability and scalability beyond dimension 20").
  S4 to S5: Sketch a plausible approach or identify the key technical barrier. This is
  what makes the direction actionable rather than aspirational.
  S6 (optional): Mention any concurrent or preliminary work that has begun to address
  this direction.

**Common pitfalls:**

(a) **Vague directions.** "More work is needed on scalability" is not actionable.
"Extending the identifiability guarantees of~\citet{X} to the nonparametric setting
requires relaxing Assumption 3.2, which currently restricts the mixing function to the
affine class" is actionable.

(b) **Wish-list directions.** "Combining method A with method B" is not a research
direction unless you explain what specific challenge makes the combination non-trivial
and what the expected benefit would be.

(c) **Directions disconnected from the survey.** Every direction should trace back to a
specific gap identified in the main body or discussion. If a direction appears in the
future work section but was never foreshadowed earlier, it feels tacked on.

(d) **Too many directions.** For a short survey, 4 to 8 well-developed directions are
better than 15 superficial ones. Each direction should be substantial enough that a
reader could plausibly start a research project from it.

### 3.7 Conclusion

The conclusion of a survey is not an abstract repeated. It should:

(1) Restate the survey's organizing principle (the taxonomy) in one sentence.
(2) State the 2 to 3 most important findings from the comparative analysis.
(3) Identify the single most pressing open problem.
(4) Optionally, state a high-level takeaway or perspective that the survey uniquely
enables.

Keep the conclusion to one paragraph (approximately 8 to 12 sentences). Do not introduce
new material.

---

## 4. Writing Individual Sections in Isolation

When the user asks to write only one section (collaborative writing), Claude adapts as
follows:

### 4.1 Information Claude Needs

Before writing any section, Claude must know:

(a) **The survey's scope**: What topic, what time range, what venues are in scope.
(b) **The taxonomy**: What are the axes and branches? If the taxonomy is not yet
designed, Claude should help design it before writing body sections.
(c) **The paper list**: What papers are being surveyed? Claude should ask for a list of
papers or a description of the literature to cover.
(d) **Notation and terminology**: Has the survey established canonical terms? If so,
what are they?
(e) **Adjacent sections**: What do the sections before and after this one cover? Claude
needs this to write appropriate transitions and avoid redundancy.
(f) **Target length**: Approximate page or word count for this section.

If any of these are missing, Claude states its assumptions and flags them.

### 4.2 Section Handoff Protocol

When writing one section of a multi-author survey:

(a) Begin with a brief "Section Brief" comment (not part of the final text) listing:
the assumed scope, the taxonomy branch this section covers, the papers included, and the
assumed notation.

(b) Write the section with explicit transition hooks: the first sentence should connect to
what the previous section likely covered, and the last sentence should set up the next
section.

(c) Flag any terminology that the section introduces for the first time. The user must
verify that this terminology is consistent with other sections.

(d) If the section references a figure or table that Claude does not have, use a
placeholder: "(see Figure~\ref{fig:taxonomy})" with a note to the user.

---

## 5. Language and Style

### 5.1 The Survey Voice

A survey voice differs from a research paper voice. In a research paper, the authors
advocate for their method. In a survey, the authors are impartial analysts. This means:

(a) Avoid evaluative language that implies the surveyor's preference: "elegantly solves"
becomes "addresses"; "unfortunately limited" becomes "limited to." Let the evidence speak.

(b) When the surveyed literature contains a genuine consensus, state it directly: "The
community has converged on X as the standard benchmark." When there is disagreement,
present both sides with evidence.

(c) Use the authorial "we" for survey-level contributions ("We organize the literature
along two axes") and third person for surveyed work ("Zhang et al. propose...").

### 5.2 Citation Density and Placement

Surveys are citation-heavy by nature, but citations must serve the argument, not replace
it.

(a) **Claim first, cite after.** "Sparsity constraints improve identifiability in
the finite-sample regime~\citep{A, B, C}" is better than "\citet{A} showed sparsity
helps. \citet{B} confirmed this. \citet{C} extended it." The first version makes an
argument; the second makes a list.

(b) **Group citations by role.** When multiple papers support the same claim, cite them
together. When papers play different roles (one proposes, another refines, a third
critiques), indicate the role: "originally proposed by~\citet{A}, later refined
by~\citet{B}, and challenged by~\citet{C} who showed..."

(c) **Citation format conventions.** Use \citet{} when the author name is part of the
sentence ("Zhang et al.~\citet{...} show that..."). Use \citep{} for parenthetical
citations at the end of a clause. Never start a sentence with a parenthetical citation.

### 5.3 Terminology Mapping

A survey's unique service includes mapping terminological variation. When different
communities use different terms for the same concept:

(a) Choose one canonical term and state it explicitly.
(b) List the variants in parentheses on first use: "We use the term *distribution shift*
(also called *domain shift*, *dataset bias*, or *covariate shift* in different
communities) to refer to..."
(c) Use only the canonical term thereafter.
(d) Consider adding a terminology mapping table if the field has more than 5 significant
terminological variations.

### 5.4 Sentence Construction

(a) Prefer active voice for survey-level claims: "We identify three failure modes" not
"Three failure modes are identified."

(b) Use passive voice for describing surveyed work when the agent is clear from context:
"The latent space is regularized via a KL penalty."

(c) Keep sentences under 35 words. Long sentences in surveys usually indicate that two
ideas need their own sentences.

(d) Avoid filler words: "itself", "actually", "basically", "essentially", "interestingly."

(e) Do not use contractions.

(f) Avoid parenthetical asides longer than 5 words. Use a separate sentence instead.

### 5.5 Paragraph Transitions

Transitions in a survey must convey logical relationships, not just sequence.

Bad: "Next, we discuss methods based on normalizing flows."
Good: "While the VAE-based methods above sacrifice exact likelihood computation for
flexible posteriors, an alternative line of work achieves exact likelihoods through
normalizing flows."

The transition should tell the reader (1) what the new paragraph relates to and (2) how
it differs from or extends the previous content.

---

## 6. Tables and Figures in Surveys

### 6.1 The Taxonomy Figure

Every survey should include a taxonomy figure. Common formats:

(a) **Tree diagram**: Best for hierarchical taxonomies with 2 to 3 levels.
(b) **Matrix/grid**: Best for two-axis taxonomies where both axes are equally important.
(c) **Venn diagram**: Best for overlapping categories (use sparingly; often a sign that
the taxonomy needs refinement).

The taxonomy figure should appear early (after the taxonomy is introduced) and be
referenced throughout the paper.

### 6.2 Comparison Tables

A well-designed comparison table is often the survey's most practical contribution. Design
principles:

(a) Rows are methods (or papers). Columns are comparison dimensions.
(b) Use checkmarks, crosses, or categorical labels rather than lengthy text.
(c) Include a "Key Insight" or "Limitation" column with one-phrase entries.
(d) Order rows by taxonomy branch, not alphabetically or chronologically.
(e) Bold or highlight the most recent or most representative method in each branch.

### 6.3 Timeline Figures

If the field has a clear evolutionary trajectory, a timeline figure showing when key
methods appeared and which methods influenced which can be valuable. Include only major
milestones (10 to 20 papers), not every surveyed paper.

---

## 7. Quality Checklist

Before finalizing any survey text, verify:

(1) No em dashes, en dashes (in prose), or bullet points appear anywhere.
(2) No section is organized paper-by-paper. Every section follows thematic organization.
(3) The taxonomy satisfies the three properties: principled axes, exhaustive coverage,
discriminative power.
(4) Every paragraph in the main body contains synthesis (comparison, assessment, or
pattern identification), not just summary.
(5) Every future direction is grounded in a specific gap identified earlier in the survey.
(6) Terminology is consistent throughout. Terminological variants are mapped explicitly.
(7) All notation is introduced in the background section before first use.
(8) Citation density is appropriate: claims are grouped with citations, not fragmented
into one-paper-per-sentence.
(9) Transitions between paragraphs convey logical relationships, not just sequence.
(10) Section lengths are approximately balanced according to the macro structure.
(11) The taxonomy figure and at least one comparison table are present (or placeholders
are flagged).
(12) No evaluative language implies the surveyor's personal preference without evidence.
(13) The conclusion does not introduce new material.
(14) Every sentence serves the survey's argument. Remove any sentence whose deletion
would not change the reader's understanding.
(15) If writing a single section in isolation, transition hooks to adjacent sections are
present and assumptions about shared context are explicitly stated.
(16) No paragraph ends with a citation dump tail (Rule 1.7). Search for "Additional
works", "Further efforts", "Related approaches have been applied to", and any sentence
listing 3+ domain applications with citations.
(17) No subsubsection has intro-closing redundancy (Rule 1.8). Check that the first
sentence of the closing does not paraphrase the intro.
(18) Shell-to-body ratio (Rule 1.9): for each subsubsection, verify that intro + closing
does not exceed 40% of total word count.
(19) Performance numbers are reported consistently: either all representative methods get
numbers, or none do (use a comparison table instead). Selective reporting looks like
promotion.
(20) Sibling \paragraph{} entries within the same \subsubsection{} should not differ by
more than approximately 2x in word count. If they do, compress the longest or split it.
(21) Cross-category synthesis paragraphs mention ALL categories, not a subset. If
analyzing four families, all four must appear.
(22) The word "Specifically" does not appear more than twice in any section. It is a
crutch for "now I will describe one paper in detail" and should be replaced with varied
transitions.

---

## 8. Anti-Patterns from Practice

This section catalogs concrete failure modes observed during real survey revision. Each
anti-pattern includes the symptom, why it fails, and the fix.

### 8.1 The Disguised Dump

**Symptom:** A paragraph ends with a sentence that replaces "Additional works..." with a
thematic opening phrase but retains the same enumeration:
  "The same paradigm has been extended to code-based scene construction via Blender
  scripts~\citep{A}, diverse physical scene types including supermarkets and digital
  replicas~\citep{B, C, D}, human behavior simulation~\citep{E}, and synthetic
  environments for visual reasoning~\citep{F, G}."

**Why it fails:** Swapping the opening phrase does not add synthesis. The reader still
sees a comma-separated list of unrelated domains with no argument connecting them.

**Fix:** Compress to one short claim with grouped citations: "Beyond indoor scenes, the
same paradigm has been extended to diverse physical substrates and perceptual
modalities~\citep{A, B, C, D, E, F, G}." Under 20 words, no per-domain enumeration.

### 8.2 The Template Paragraph

**Symptom:** Paragraph follows a rigid structure:
  [1 topic sentence defining the category]
  [Paper A description, 1 to 2 sentences]
  [Paper B description, 1 to 2 sentences]
  [Paper C description, 1 to 2 sentences]
  ["Specifically, Paper D does..." detailed description]

**Why it fails:** This is paper-by-paper organization wearing a topic-sentence disguise.
The topic sentence provides a label, not an argument. Each paper is described
independently without comparison.

**Fix:** Restructure around a methodological tension or design question. For example,
instead of listing four methods, frame the paragraph around "the central design tension
is whether to tokenize observations or generate them in continuous space," then let papers
appear as evidence for each side.

### 8.3 The "Specifically" Crutch

**Symptom:** Multiple paragraphs in the same section use "Specifically, [Paper X]
does..." as a transition to a detailed example.

**Why it fails:** When every paragraph uses the same transition, it becomes a tic rather
than a rhetorical device. It signals "I am about to describe one paper in detail" rather
than connecting the example to the argument.

**Fix:** Replace with varied transitions that explain WHY this example matters:
  "X exemplifies the minimal version of this paradigm: ..."
  "The most systematic realization of this principle converts..."
  "The challenge is best illustrated by X, which..."
  Or simply delete "Specifically," and start with the paper name.

### 8.4 The Overstuffed Single Paragraph

**Symptom:** A subsubsection has only one \paragraph{} heading, sandwiched between a
long intro and a long closing. The single paragraph internally covers 2 to 3 distinct
methodological threads without structure.

**Why it fails:** The intro and closing shell becomes disproportionate. The single
paragraph tries to do too much, resulting in either paper-by-paper listing or rapid
topic switching.

**Fix:** Identify the distinct methodological threads within the paragraph and split into
two \paragraph{} headings. For example, if the paragraph covers both "static simulation"
and "co-evolutionary simulation," split them. Each \paragraph{} should have one clear
claim.

### 8.5 Selective Performance Promotion

**Symptom:** Some papers get specific numbers ("achieves 51% on SWE-Bench Verified",
"1.46 mean human-normalized score") while most get only qualitative claims. The
selection of which papers get numbers appears arbitrary.

**Why it fails:** It makes the survey look like it is promoting certain papers over
others. Reviewers will notice and question the authors' neutrality.

**Fix:** Choose one strategy and apply consistently: (a) remove all specific numbers
from prose and state qualitative claims only, reserving numbers for a comparison table,
or (b) report numbers for ALL representative methods in each paragraph. Option (a) is
usually simpler and preferred.

### 8.6 The Incomplete Cross-Category Synthesis

**Symptom:** A cross-category analysis paragraph discusses three out of four categories,
omitting one because its fidelity challenge is different or less obvious.

**Why it fails:** The reader expects comprehensive coverage in a synthesis paragraph. An
omission suggests the author forgot or could not find anything to say.

**Fix:** Every category must appear. If a category's challenge is different in kind (e.g.,
programmatic environments have execution fidelity rather than physical fidelity), state
this difference explicitly rather than omitting the category.

### 8.7 Framing Multiple Methods as a List vs. as Strategies

**Symptom:** A paragraph presents three methods sequentially:
  "Method A does X. Method B does Y. Method C also provides Z."

**Why it fails:** The reader sees a list, not an argument. The methods may actually
represent complementary strategies for the same problem, but the sequential presentation
hides this structure.

**Fix:** Frame as strategies for a shared challenge: "Two complementary strategies have
emerged. The first is [strategy name]: [methods A, B as evidence]. The second is
[strategy name]: [method C as evidence]. [Optional: cross-cutting enabler that serves
both strategies.]" This gives the reader a conceptual framework, not just a list.