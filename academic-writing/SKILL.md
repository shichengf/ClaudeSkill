---
name: academic-writing
description: >
  Skill for rigorous academic writing in ML/AI research contexts: drafting and revising
  conference papers, rebuttals, supplementary materials, and responses to reviewers.
  Trigger this skill whenever the user asks to write, revise, or review any academic text
  including paper sections (abstract, introduction, method, experiments, related work,
  conclusion), rebuttal letters, author responses, cover letters to editors, or any
  formal scientific prose. Also trigger when the user asks to check academic writing for
  rigor, consistency, or formatting compliance. This skill enforces strict conventions
  from top ML venues (ICML, NeurIPS, ICLR, AAAI, CVPR, ACL, etc.) and ensures
  self-consistency, notational discipline, and professional tone throughout.
---

# Academic Writing Skill

This skill governs all academic writing output. Every sentence Claude produces under this
skill must meet the standards of a top-tier ML conference submission. The overarching
philosophy: **precision over flair, substance over rhetoric, and internal consistency
above all else**.

---

## 1. Foundational Principles

### 1.1 Rigor and Precision

Academic writing is not persuasive essay writing. Every claim must be either (a) supported
by a citation, (b) derived from the paper's own theory or experiments, or (c) explicitly
flagged as a hypothesis or conjecture. Avoid vague hedging that adds no information (e.g.,
"it is well known that" without a citation is meaningless). If something is well known,
cite the source that established it.

Quantitative claims require numbers. "Our method significantly outperforms the baseline"
is incomplete without specifying the metric, the numerical gap, and ideally a statistical
significance test or confidence interval. Replace adjectives with data whenever possible.

### 1.2 Self-Consistency

Self-consistency is the single most important quality of a credible academic paper. A
paper that contradicts itself signals carelessness and destroys reviewer trust. Before
producing any text, Claude must verify that:

(a) Terminology is used identically throughout. If "domain label" is introduced in
Section 3, it must not become "domain index" in Section 5 without explicit redefinition.

(b) Notation is stable. If $\mathbf{z}_t$ denotes the latent variable in the method
section, it must not silently become $z_t$ or $\mathbf{h}_t$ elsewhere.

(c) Experimental claims in the rebuttal do not contradict those in the main paper. If the
paper reports a baseline score of 0.921, the rebuttal must not cite 0.925 for the same
number without explanation.

(d) Theoretical claims and experimental framing are aligned. If the identifiability theory
requires domain-specific priors, the experiments must not inadvertently argue that
domain-specific priors are unimportant.

### 1.3 Prose Must Match Adjacent Data

When a paragraph follows a table, every numerical claim in the prose must exactly match
the table. If a table shows 0.925 for a specific configuration, the following prose must
not round this to ">0.98" or state any number that contradicts the table entry. This type
of error is especially dangerous because the reviewer reads the table and prose together;
a mismatch signals either carelessness or dishonesty.

### 1.4 Distinguish Proved Claims from Empirical Observations

A theoretical result that has been formally proved ("Theorem 4.1 guarantees...") and an
empirical observation ("We observe that...") require different language. If a claim is
supported only by experiments, use hedged phrasing: "Empirically, the binding constraint
appears to be $K_{\text{active}} \leq d+1$." If the claim is proved, cite the theorem
directly. Presenting empirical observations with the certainty of proved theorems is a
common credibility trap.

### 1.5 Every Experiment Needs a Takeaway

Never present experimental results without an explicit conclusion. A table or number alone
is not an argument. After every experiment, state what the reader should learn from it in
one sentence. Bad: "At 10% data, Corr($K=3$) stays at 0.96." (a number without
interpretation). Good: "Trajectory recovery degrades more gracefully than MCC: at 10%
data, MCC drops to 0.75 while Corr($K=3$) remains at 0.96, because temporal smoothing
(Theorem 4.3) averages out per-step noise." (number, comparison, and causal explanation).

### 1.6 Argumentative Structure

Every paragraph serves exactly one function: it either (a) states a claim, (b) provides
evidence for a claim, or (c) transitions between claims. Paragraphs that attempt to do all
three at once become muddled. When writing or revising, identify the function of each
paragraph and ensure it fulfills that function cleanly.

In rebuttals specifically, every paragraph must respond to a concrete reviewer concern.
Generic padding ("We thank the reviewer for their insightful comments") wastes character
budget. Get to the substance immediately.

---

## 2. Formatting Rules (Non-Negotiable)

These rules are absolute and apply to all output produced under this skill.

### 2.1 No Dashes

Never use em dashes, en dashes, or any dash-like punctuation as a stylistic device.
This includes:

(a) Em dash as parenthetical: "The method — which we call TRACE — achieves..." is
**forbidden**. Rewrite using commas, parentheses, or a separate sentence: "The method,
which we call TRACE, achieves..." or "Our method (TRACE) achieves..."

(b) En dash as a range indicator in prose: In running text, write "from 5 to 10" instead
of "5–10". The en dash is acceptable only inside tables, figures, or parenthetical
numerical ranges like "(5--10)" in LaTeX.

(c) Dash as an informal connector: "Fast training, good results — what more could you
want?" is never appropriate in academic writing.

### 2.2 No Unordered Lists

Never use bullet points or unordered lists in academic prose. This includes Markdown
bullet points (`-`, `*`, `+`) and any visual equivalent. Academic text flows in complete
paragraphs and sentences.

When enumerating items, use one of the following ordered structures:

(a) Inline enumeration with explicit markers: "We identify three failure modes: (1)
insufficient data diversity, (2) numerical instability in the projection step, and (3)
sensitivity to hyperparameter K."

(b) Labeled enumeration in display format, where each item is a complete sentence or
paragraph, introduced by a letter or number label such as (a), (b), (c) or (1), (2), (3).

(c) A "Remark" or "Observation" environment for standalone points in a theoretical
section.

The reason for this rule: unordered bullet points signal informality. They fragment the
argument into disconnected pieces and make it easy to hide logical gaps. Ordered
enumeration forces the writer to consider the sequence and relationship between items.

Italicized labels without ordering markers (e.g., "*Label noise:*" and "*Mechanism
impurity*" as standalone items) are a borderline violation. Convert to (a)/(b) or (i)/(ii).

### 2.3 Symbol and Notation Discipline

Every mathematical symbol must be formally introduced before its first use. "Let $K$
denote the number of domains" must precede any equation or sentence that uses $K$. This
applies to all single-letter variables without exception.

Specific requirements:

(a) Greek letters: State what each one represents on first use. "$\sigma_{\min}$" is
meaningless until you write "where $\sigma_{\min}$ denotes the smallest singular value of
the basis matrix $\mathbf{B}$."

(b) Subscripts and superscripts: Define the indexing convention. If $i$ indexes data
points and $k$ indexes domains, state this once in the notation section or at first use,
and never swap them.

(c) Bold vs. non-bold: Be consistent. If vectors are bold ($\mathbf{z}$) and scalars are
not ($z$), maintain this throughout. Mixing conventions within a single document is a
serious error.

(d) Operator notation: If you use $\|\cdot\|$ for a norm, specify which norm (e.g.,
"$\|\cdot\|_2$ denotes the Euclidean norm").

(e) Reusing symbols: Never reuse a symbol for two different purposes in the same document.
If $T$ is the number of time steps, it cannot also be a transformation matrix.

(f) Introduce-and-discard: Do not introduce a new variable (e.g., $s$) only to equate it
immediately to an existing one ($K_{\text{active}}$) and never use it again. Write "only
$K_{\text{active}}$ entries are nonzero" instead of "is $s$-sparse (only
$s = K_{\text{active}}$ mechanisms are active)."

### 2.4 Term Definition Protocol

Every technical term or coined phrase must be explicitly defined at its first occurrence.
This includes:

(a) Novel terms introduced by the paper: "We define *mechanism trajectory* as the
continuous path $\alpha(t)$ through the space of mixing coefficients."

(b) Terms borrowed from adjacent fields that the expected audience may not know: If you
use "sufficient variability" from the nonlinear ICA literature, provide a one-sentence
gloss and a citation.

(c) Abbreviations: Spell out on first use, then use the abbreviation consistently. "Causal
Representation Learning (CRL)" becomes "CRL" for all subsequent occurrences. Never
re-expand after the first definition unless starting a new major document (e.g., a
separate rebuttal letter). Common abbreviations that may not be known to all reviewers
(DGP, OOD, SNR) must also be expanded on first use.

### 2.5 Figure and Table References

Every reference to a figure or table must specify its location. This means:

(a) In a paper: "as shown in Figure 3 (left panel)" or "see Table 2, column 3". Never
write "as shown in the figure" or "see the table below" because reviewers may be reading
a differently-paginated version.

(b) In a rebuttal: If referring to a figure in the main paper, write "Figure 3 in the
main paper". If referring to a new figure in the rebuttal, write "Figure R1 (attached
below)" and ensure it is actually present. If the venue does not permit figures in
rebuttals, note this constraint explicitly.

(c) Cross-referencing: When a rebuttal references a specific table entry, cite the row and
column: "the MCC score of 0.984 reported in Table 1, row 'Ours', column 'd=64'."

---

## 3. Paper Writing Logic

### 3.0 Section-Level Blueprinting (Overarching Principle)

Before writing any section, produce a **sentence-level blueprint** that specifies the
role of each sentence or sentence group. A blueprint is a short ordered list such as:

(a) Related Work: paradigm → limitation → our distinction
(b) Introduction: broad motivation → specific gap → prior attempts and their
shortcomings → our approach → contributions list
(c) Method: problem setup → intuition/overview → component 1 → component 2 → full
algorithm
(d) Experiments: research questions → setup → results by question → ablations →
limitations

Within each blueprint slot, further specify the approximate number of sentences. For
example, a Related Work paragraph blueprint might read:

  S1--S3: Define the paradigm and cite foundational work.
  S4--S5: Expand two representative learning-based methods with limitations.
  S6: Group remaining works by shared limitation with merged citations.
  S7: Distinguish our approach.

This blueprint should be drafted (mentally or in comments) before any prose is written.
It prevents two failure modes: (a) sections that meander without clear argumentative
progression, and (b) sections where paragraph lengths are wildly unbalanced because the
writer did not plan how much space each point deserves.

When revising, check the existing text against its blueprint. If a sentence does not
clearly serve one of the blueprint slots, it is either misplaced or unnecessary.

The following subsections provide concrete blueprints for each standard section.

### 3.1 Abstract

The abstract follows a rigid four-part structure in roughly 150 to 250 words:

(1) **Problem**: One or two sentences establishing the research gap. Be specific about
what is missing, not about what exists.

(2) **Approach**: Two to three sentences describing the proposed method at a conceptual
level. Name the method. State the key idea that distinguishes it from prior work.

(3) **Theory/Guarantee**: One sentence on the theoretical contribution, if any. State what
is proved and under what conditions.

(4) **Results**: One to two sentences on empirical findings. Include at least one concrete
number.

### 3.2 Introduction

The introduction expands the abstract into roughly 1.5 pages. It follows a funnel
structure with a sentence-level blueprint for each paragraph:

**P1: Vision and Background** (broad motivation → narrow the scope, ~1 paragraph)
  S1--S2: Broad area and recent progress.
  S3--S4: Narrow to the specific capability gap your work addresses.

**P2: The Problem with the Status Quo** (what exists → why it fails, ~1 paragraph)
  S1: State the prevailing approach (e.g., human authoring, static tool libraries).
  S2--S3: Present empirical or logical evidence that it is insufficient.
  S4: Optionally state a hypothesis for *why* it fails (e.g., human--machine
  misalignment).

**P3: Why Existing Solutions Fall Short** (prior attempts → their limitations, ~1
paragraph)
  S1: Acknowledge recent attempts to solve the problem, with citations.
  S2--S3: Identify the fundamental limitation shared by these attempts (e.g., tool vs.
  skill gap, ground-truth dependency). Cite concurrent work here if relevant.

**P4: Our Approach** (key idea → how it works, ~1 paragraph)
  S1: "To address these challenges, we propose [method name]."
  S2--S4: Describe the two or three core design decisions at a conceptual level. Each
  design decision should map to one limitation identified in P3.

**P5: Contributions** (explicit ordered list, ~0.5 paragraph)
  Use "(1) We propose..., (2) We demonstrate..., (3) We achieve..." format.
  Each contribution should be concrete and verifiable, not vague. Include at least one
  number in the empirical contribution.

### 3.3 Method Section

The method section must be self-contained: a reader should be able to reimplement the
method from this section alone (plus the appendix for proof details).

**P1: Problem Setup** (~0.5--1 paragraph)
  S1--S2: Formally define the input, output, and objective.
  S3--S4: Introduce all notation. Every symbol must appear here before it is used later.

**P2: Method Overview** (~1 paragraph)
  S1: One-sentence summary of the full pipeline.
  S2--S4: Name each component and state its role in one sentence each. This paragraph
  serves as a roadmap so the reader knows what is coming before the details.

**P3--P_n: Component Details** (~1 subsection per component)
  For each component, follow: intuition (why this component is needed, 1--2 sentences)
  → formal definition (equations, algorithms) → design choices and justification
  (why this design over alternatives, 1--2 sentences).

**Final: Full Algorithm** (pseudocode or formal procedure)
  Summarize the entire pipeline as Algorithm 1 so the reader can see how the components
  fit together.

### 3.4 Experiments Section

**P1: Research Questions** (1--3 sentences)
  Explicitly state the RQs the experiments will answer. Number them: "We aim to answer:
  (1) Does \method improve...? (2) How does each component contribute...? (3) Do the
  results transfer...?"

**P2: Setup** (~1 paragraph)
  S1--S2: Datasets and benchmarks (with citations and sizes).
  S3: Baselines (name each, one sentence explaining why it is a fair comparison).
  S4: Metrics (define any non-standard metric).
  S5: Key hyperparameters and compute budget.

**P3--P_n: Results by Research Question** (~1 subsection per RQ)
  For each RQ: state the finding in one topic sentence → present the supporting table or
  figure → provide a takeaway sentence explaining *why* the result holds (not just *what*
  the numbers are). Organize by research question, not by dataset.

**Ablations** (~1 subsection)
  Isolate the contribution of each component by removing it. Each ablation row in the
  table needs a one-sentence interpretation.

**Limitations** (1--2 sentences, honest)
  State what the experiments do not cover and why. This preempts reviewer criticism and
  signals maturity.

### 3.5 Related Work

Related work is not a literature dump. It is a structured argument showing why existing
work is insufficient and why your contribution is necessary.

#### 3.5.1 Macro Structure

Organize by *conceptual themes*, not by chronology or by individual paper. Each
`\paragraph{}` covers one theme (e.g., "Agent skills" and "Self-evolving agents"). Aim
for roughly balanced paragraph lengths; if one paragraph is twice the length of another,
restructure.

#### 3.5.2 The "Expand-Two, Group-the-Rest" Pattern

A common and effective strategy for covering a large body of related work concisely:

(a) **Pick two representative papers to expand** (1--2 sentences each, describing method
and limitation).

(b) **Group the remaining papers by shared limitation** and cite them together in a single
sentence. For example: "Voyager~\citep{A}, Yunjue~\citep{B}, and TTE~\citep{C} all
synthesize atomic tool functions; none, however, can construct the interdependent
multi-file structure a full skill package demands." This is far more effective than
describing each paper individually with its own limitation sentence.

(c) When multiple papers share the same limitation, **merge citations into one clause**
rather than writing separate "X does A; however, B" sentences for each. Bad: three
consecutive sentences each ending with "however, it cannot handle multi-file packages."
Good: one sentence citing all three, followed by the shared limitation once.

#### 3.5.3 Sentence Variety

Never use the same "method + however + limitation" template for consecutive papers.
Alternate between:

(a) Concessive clauses: "While X achieves ..., the resulting skills are ..."
(b) Contrast: "Unlike X which ..., Y takes a different route by ..."
(c) Concession: "Although X demonstrates ..., it relies on ..."
(d) Group + summary: "A, B, and C all produce ...; none, however, can ..."

#### 3.5.4 Do Not Announce Structure

Do not write meta-structural sentences like "existing methods exhibit three recurring
limitations" or use transitions like "On the first front." These read like presentation
slides, not research prose. Instead, let the reader discover the structure through the
argument itself. A sentence like "Moving beyond atomic tool generation, several methods
distill higher-level behavioral knowledge" is acceptable because it describes *content*,
not *structure*.

#### 3.5.5 Closing Sentences Across Paragraphs

Each paragraph should end by distinguishing your approach, but the closing sentences of
different paragraphs must emphasize *different aspects* of your contribution. If one
paragraph closes by highlighting your generation mechanism (e.g., "iterative co-evolution
of multi-file packages"), the other should highlight a different design choice (e.g.,
"information isolation to prevent confirmation bias"). Repeating the same distinction
verbatim across paragraphs signals shallow writing.

#### 3.5.6 Concurrent and Closely Named Work

(a) If a concurrent work shares a similar name or scope, mark it explicitly: "the
concurrent work X~\citep{...}" on first mention.

(b) Ensure \citep{} keys are consistent across the entire paper (introduction, related
work, experiments). Duplicate BibTeX entries with different keys for the same paper will
cause the reference to appear twice in the bibliography.

#### 3.5.7 Recurring Phrases

Key distinguishing phrases (e.g., "structured multi-file skill packages") should appear
at most twice in the entire Related Work section. Overuse dilutes their impact and makes
the prose feel templated.

---

## 4. Rebuttal Craft

### 4.1 Strategic Principles

A rebuttal is not a defense; it is a technical clarification. The goal is to resolve
misunderstandings and provide new evidence, not to argue that the reviewer is wrong.

(a) **Prioritize factual corrections**: If a reviewer misunderstands the method, correct
the misunderstanding with a precise quote from the paper plus clarification. Do not
paraphrase the reviewer's concern in a way that softens it; address it directly.

(b) **New experiments must be airtight**: Any new result introduced in a rebuttal will
receive extra scrutiny. Verify that new numbers are internally consistent and do not
contradict the main paper. If a new experiment shows surprisingly strong results, work out
the mathematics of why before including it.

(c) **Character budget discipline**: Most venues impose strict character limits (e.g.,
5000 characters for ICML 2026). Every sentence must earn its place. Cut all padding,
acknowledgments, and redundant restatements of the reviewer's concern. When trimming,
prioritize cutting (in order): sycophantic openings, generic future direction speculation,
surface-level application examples, and verbose closing sentences.

(d) **Cross-rebuttal consistency**: All rebuttals for the same paper must use identical
numbers, terminology, and framing. If one rebuttal says the baseline scores 0.921 and
another says 0.925, the reviewers will notice.

### 4.2 Make the Reviewer's Life Easy

Reviewers handle dozens of papers. The easier you make it for them to verify your claims,
the more likely they are to engage positively. Concrete rules:

(a) **Inline everything**: Never say "see Appendix D.3 for details." Summarize the key
idea from the appendix in one or two sentences so the reviewer does not need to leave the
rebuttal. If the proxy is the ratio of vertical to total velocity, say so directly rather
than pointing elsewhere.

(b) **Describe experimental procedures specifically**: Do not say "we test label noise."
Say "we randomly flip 20% of training samples' domain labels to a uniformly chosen
incorrect domain." The reviewer should be able to picture the experiment from the rebuttal
alone.

(c) **Merge related concerns under one heading**: If a reviewer lists Weakness 1 and Key
Question (a) that address the same underlying issue, respond once under a combined heading
rather than artificially separating them. This avoids repetition and shows you understand
the reviewer's actual concern.

(d) **Revision promises must say HOW**: "Line 090 revised" is useless. "Line 090 revised
to state that TRACE proves recoverability under the convex combination assumption, rather
than claiming the assumption is physically inherent" is actionable.

### 4.3 Rebuttal Strategy by Reviewer Type

Reviewers differ in their stance and expectations. Tailor the rebuttal accordingly:

(a) **Critical reviewer (low score, specific technical objections)**: Focus entirely on
addressing the objections with evidence. Every sentence should resolve a specific concern.
Avoid padding. If the reviewer says "I will raise my score if X," then X must be the
central focus of the rebuttal.

(b) **Skeptical reviewer (low score, broad concerns about applicability)**: Provide new
experiments that directly test the concern. Theoretical arguments alone will not persuade;
empirical evidence is necessary. Show that the method works under weakened assumptions.

(c) **Supportive reviewer (high score, no specific objections)**: This reviewer is a
potential champion for the paper. Frame new experiments as strengths of the method, not
just as responses to other reviewers. Give them concrete ammunition: "TRACE demonstrates
robustness to 50% domain impurity (Weight Corr >0.96), simplex-constrained recovery
outperforms unconstrained by +0.015 in correlation, and sample efficiency degrades
gracefully (Corr >0.96 at 10% training data)." Each result should read as a reason this
paper deserves acceptance.

(d) **Silent reviewer (medium score, minimal feedback)**: Proactively address the most
likely unstated concerns (often overlap with other reviewers' points). Be concise; this
reviewer may not engage deeply during discussion.

### 4.4 Cross-Rebuttal Audit Protocol

Before submitting rebuttals, perform a systematic cross-rebuttal audit:

(a) **Numerical consistency**: Extract every number from all rebuttals and verify that
identical experiments yield identical numbers everywhere.

(b) **Isolated data points**: If an experimental result appears in only one rebuttal (but
not in the others that discuss related topics), this creates suspicion when reviewers
cross-read. Either include the result in all relevant rebuttals, or remove it.

(c) **Terminology alignment**: The same metric must have the same name everywhere. If one
rebuttal calls it "Weight Corr" and another calls it "α-Corr," reviewers will notice.

(d) **Framing alignment**: If one rebuttal presents a result as a limitation while another
presents the same result as a strength, the contradiction undermines both.

### 4.5 Structure of a Rebuttal

For each reviewer concern, use this structure:

(1) One-sentence summary of the concern (paraphrased, not quoted).
(2) Direct response with evidence: a clarification, a citation to the paper, or new
experimental data.
(3) Explicit takeaway: what the reviewer should conclude from the evidence.
(4) If applicable, a concrete revision plan: "We will add this clarification to Section X
in the revision."

Group related concerns under a single heading when they share an underlying issue. Use
ordered labels (Q1, Q2, Q3 or W1, W2, W3) that match the reviewer's numbering when
possible.

### 4.6 Common Pitfalls

(a) **Claiming robustness that is architecturally trivial**: If the model's encoder does
not use domain labels as input, then robustness to domain label noise is a trivial
consequence of the architecture, not a meaningful empirical finding. Presenting it as the
latter damages credibility. Report the result, but do not claim causal attribution (e.g.,
do not say "the transition prior provides a meaningful identifiability signal" when the
true reason is that the encoder ignores labels).

(b) **Surprisingly strong results without explanation**: If a degradation experiment (e.g.,
50% contamination) produces unexpectedly good results, explain WHY mathematically before
the reviewer asks. For example, if contamination at ε=50% with K=5 domains still
preserves each domain's specific signal because the critical threshold is ε=(K−1)/K=80%,
state this explicitly. An unexplained strong result invites scrutiny of the experimental
design itself.

(c) **Non-monotonic results**: If a degradation experiment (e.g., increasing contamination
from 0% to 50%) produces non-monotonic metrics, this is a red flag. Either the experiment
has a bug, or there is a mathematical explanation (e.g., symmetric label noise preserving
partial signal). Either way, the non-monotonicity must be explained, not hidden.

(d) **Overly strong claims**: "Our method is the first to..." should be verified
exhaustively. "To the best of our knowledge, our method is the first to..." is safer but
still requires a thorough literature search.

(e) **Undermining your own theory**: If the theoretical contribution requires assumption
A, the experiments must not inadvertently argue that assumption A is unimportant. Every
empirical framing choice should be checked for consistency with the theoretical claims.

(f) **Answering the question that was asked, not an adjacent one**: Read the reviewer's
question literally. If they ask "how to handle K≫d without increasing d," a table showing
improvement as d increases does not answer the question. Provide evidence at fixed d.

(g) **Listing a small fixed number of applications**: Enumerating exactly N use cases
(e.g., "three domains: manufacturing, clinical, autonomous") can backfire by implying the
method is limited to those N domains. Either provide a principled characterization of the
class of applicable problems, or give a broader framing: "domains where pure-regime data
is abundant but transitions are scarce, such as manufacturing, clinical settings, and
autonomous systems."

(h) **Overconfident real-world claims**: Stating "10-20% impurity is realistic in
practice" without citation or evidence is a credibility risk. The reviewer may ask "How do
you know?" If you cannot back a real-world applicability claim with a reference or data,
soften it or remove it.

### 4.7 Rebuttal Tone

Be direct, factual, and respectful. Avoid:

(a) Sycophantic openings ("We sincerely thank the reviewer for their valuable time and
constructive feedback"). Reviewers see through this and it wastes characters.

(b) Defensive language ("We respectfully disagree with the reviewer's characterization").
Instead, state the fact: "The paper uses lag-L, not lag-1 (see Equation 5, Section 3.2)."

(c) Vague promises ("We will improve the writing in the revision"). Be specific: "We will
add a paragraph in Section 4.1 clarifying the distinction between training-time and
inference-time K-selection."

(d) Lobbying for score changes ("We would be grateful for reconsideration of the score").
Let the evidence speak. If the reviewer said they would raise their score, do not quote
this back at them.

---

## 5. Language and Style

### 5.1 Sentence Construction

(a) Prefer active voice for claims about the paper's contributions: "We prove that..." not
"It is proved that..."

(b) Use passive voice sparingly, only when the agent is genuinely irrelevant: "The model
is trained for 100 epochs" is acceptable.

(c) Keep sentences under 35 words when possible. Long sentences in academic writing
usually indicate that two ideas have been fused into one.

(d) Avoid parenthetical asides that span more than 5 words. If the aside is important
enough to include, it deserves its own sentence.

(e) Avoid filler words: "itself," "actually," "basically," "essentially." If removing the
word does not change the meaning, remove it.

### 5.2 Word Choice

(a) Prefer precise verbs over vague ones: "achieves" over "gets", "demonstrates" over
"shows", "requires" over "needs".

(b) Avoid informal intensifiers: "very", "really", "quite", "extremely". In academic
writing, intensity comes from data, not adverbs.

(c) Avoid redundant phrasing: "in order to" becomes "to"; "due to the fact that" becomes
"because"; "a total of 5 experiments" becomes "5 experiments".

(d) Do not use contractions in formal academic text.

(e) Use "approximately" instead of "~" in prose. The tilde is acceptable in tables and
inline with numbers in parentheses, but not in running text.

### 5.3 Paragraph Transitions

Every paragraph must connect to the preceding one. Use explicit logical connectors: "In
contrast to the discrete formulation above, we now consider...", "Building on Theorem 4.1,
we derive...", "While the above addresses identifiability, we now turn to estimation
error."

Avoid generic transitions like "Next, we discuss..." or "In this section, we present..."
These tell the reader nothing about the logical relationship between paragraphs.

---

## 6. Pre-Submission Checklist

Before finalizing any academic text, verify the following:

(1) Every symbol is defined before first use.
(2) Every technical term is defined at first occurrence.
(3) Every figure and table reference includes a location specifier.
(4) No em dashes, en dashes (in prose), or unordered bullet points appear anywhere.
(5) All numbers are internally consistent across sections and across rebuttals.
(6) Every claim is supported by a citation, a theorem, or experimental evidence.
(7) The abstract, introduction, method, and conclusion tell a coherent and
non-contradictory story.
(8) Rebuttal framing does not inadvertently undermine the paper's theoretical
contributions.
(9) New experimental results in rebuttals are mathematically scrutinized for plausibility
before inclusion.
(10) Character limits are respected (count raw characters including markdown formatting
for venues that specify character limits).
(11) Prose claims immediately following a table match the table's numbers exactly.
(12) No experimental result appears in only one rebuttal when multiple rebuttals discuss
the same topic (cross-rebuttal isolation check).
(13) Empirical observations are not stated with the certainty of proved theorems.
(14) No variable is introduced solely to be equated to another and never reused.
(15) Every experiment has an explicit takeaway sentence, not just numbers.
(16) No revision promise is vague: each states what will change and how.
(17) No reference to appendix/supplement without also inlining the key idea.
