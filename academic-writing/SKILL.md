---
name: academic-writing
description: >
  Skill for rigorous academic writing in ML/AI research contexts: drafting and revising conference papers, supplementary materials, and visual evidence. Trigger this skill whenever the user asks to write, revise, or review paper text, figures, plots, tables, captions, accessibility descriptions, or supplementary appendices. Also trigger for checks of rigor, consistency, visual legibility, information design, or formatting compliance. Enforces strict conventions from top ML venues (ICML, NeurIPS, ICLR, AAAI, CVPR, ACL, EMNLP, etc.) and ensures self-consistency, notational discipline, and professional tone throughout. For rebuttals, author responses, and reviewer replies, use the rebuttal-craft skill instead (which layers on top of this one).
---

# Academic Writing Skill

This skill governs all academic writing output. Every sentence Claude produces under this skill must meet the standards of a top-tier ML conference submission. The overarching philosophy: **precision over flair, substance over rhetoric, and internal consistency above all else**.

For rebuttals and author responses, also invoke the rebuttal-craft skill, which layers rebuttal-specific strategy on top of these baseline rules.

---

## 1. Foundational Principles

### 1.1 Rigor and Precision

Academic writing is not persuasive essay writing. Every claim must be either (a) supported by a citation, (b) derived from the paper's own theory or experiments, or (c) explicitly flagged as a hypothesis or conjecture. Avoid vague hedging that adds no information (e.g., "it is well known that" without a citation is meaningless). If something is well known, cite the source that established it.

Quantitative claims require numbers. "Our method significantly outperforms the baseline" is incomplete without specifying the metric, the numerical gap, and ideally a statistical significance test or confidence interval. Replace adjectives with data whenever possible.

Feedback from senior collaborators and advisors is high-signal but not infallible. Apply the suggestion's intent without inheriting its risk vectors: requests to add overclaiming language ("novel", "first", "SOTA") or to remove building-block citations under the guise of "stronger framing" should be evaluated against the evidence the paper actually provides. Push back with concrete reasons when warranted. See §5.4 for specifics.

### 1.2 Self-Consistency

Self-consistency is the single most important quality of a credible academic paper. A paper that contradicts itself signals carelessness and destroys reviewer trust. Before producing any text, Claude must verify that:

(a) Terminology is used identically throughout. If "domain label" is introduced in Section 3, it must not become "domain index" in Section 5 without explicit redefinition.

(b) Notation is stable. If $\mathbf{z}_t$ denotes the latent variable in the method section, it must not silently become $z_t$ or $\mathbf{h}_t$ elsewhere.

(c) Story framing is stable across sections. If the Introduction frames the contribution along axis A, the Abstract, Conclusion, and section headers must not silently reframe along axis B. When a framing is replaced, audit the rest of the paper for residual phrasings of the old framing (see §5.1 for the recipe).

(d) Theoretical claims and experimental framing are aligned. If the identifiability theory requires domain-specific priors, the experiments must not inadvertently argue that domain-specific priors are unimportant.

### 1.3 Prose Must Match Adjacent Data

When a paragraph follows a table, every numerical claim in the prose must exactly match the table. If a table shows 0.925 for a specific configuration, the following prose must not round this to ">0.98" or state any number that contradicts the table entry. This type of error is especially dangerous because the reviewer reads the table and prose together; a mismatch signals either carelessness or dishonesty.

### 1.4 Distinguish Proved Claims from Empirical Observations

A theoretical result that has been formally proved ("Theorem 4.1 guarantees...") and an empirical observation ("We observe that...") require different language. If a claim is supported only by experiments, use hedged phrasing: "Empirically, the binding constraint appears to be $K_{\text{active}} \leq d+1$." If the claim is proved, cite the theorem directly. Presenting empirical observations with the certainty of proved theorems is a common credibility trap.

### 1.5 Every Experiment Needs a Takeaway

Never present experimental results without an explicit conclusion. A table or number alone is not an argument. After every experiment, state what the reader should learn from it in one sentence. Bad: "At 10% data, Corr($K=3$) stays at 0.96." (a number without interpretation). Good: "Trajectory recovery degrades more gracefully than MCC: at 10% data, MCC drops to 0.75 while Corr($K=3$) remains at 0.96, because temporal smoothing (Theorem 4.3) averages out per-step noise." (number, comparison, and causal explanation).

### 1.6 Argumentative Structure

Every paragraph serves exactly one function: it either (a) states a claim, (b) provides evidence for a claim, or (c) transitions between claims. Paragraphs that attempt to do all three at once become muddled. When writing or revising, identify the function of each paragraph and ensure it fulfills that function cleanly.

### 1.7 Quantitative Language Must Match Measurement Scope

Quantitative adjectives such as "millisecond-scale", "orders of magnitude faster", "Nx slower", or "second-scale" carry implicit measurement claims. They are only permissible in sections where you have actually measured the corresponding quantity at that magnitude.

For example, if your paper reports end-to-end training time wall clock but never isolated per-call latency, the Introduction may not claim "per-call cost is orders of magnitude below a neural verifier" — that requires per-call latency measurement. Use safer qualitative comparisons ("far below", "well below", "much cheaper") when the precise scale is not measured.

When recycling quantitative language from a measurement section into the Introduction or Abstract, verify that the body section actually carries data at that scale. The reader will check; an unbacked "orders of magnitude" claim is a credibility leak.

---

## 2. Formatting Rules (Non-Negotiable)

These rules are absolute and apply to all output produced under this skill.

### 2.0 Source Line Layout

Keep each prose paragraph on one physical source line in LaTeX and Markdown. Do not hard-wrap prose at a fixed column width. Retain line breaks only when required by syntax or layout, including environment boundaries, tables, equations, algorithms, code blocks, and explicit line-break commands.

### 2.1 No Dashes

Never use em dashes, en dashes, or any dash-like punctuation as a stylistic device. This includes:

(a) Em dash as parenthetical: "The method — which we call TRACE — achieves..." is **forbidden**. Rewrite using commas, parentheses, or a separate sentence: "The method, which we call TRACE, achieves..." or "Our method (TRACE) achieves..."

(b) En dash as a range indicator in prose: In running text, write "from 5 to 10" instead of "5–10". The en dash is acceptable only inside tables, figures, or parenthetical numerical ranges like "(5--10)" in LaTeX.

(c) Dash as an informal connector: "Fast training, good results — what more could you want?" is never appropriate in academic writing.

### 2.2 No Unordered Lists

Never use bullet points or unordered lists in academic prose. This includes Markdown bullet points (`-`, `*`, `+`) and any visual equivalent. Academic text flows in complete paragraphs and sentences.

When enumerating items, use one of the following ordered structures:

(a) Inline enumeration with explicit markers: "We identify three failure modes: (1) insufficient data diversity, (2) numerical instability in the projection step, and (3) sensitivity to hyperparameter K."

(b) Labeled enumeration in display format, where each item is a complete sentence or paragraph, introduced by a letter or number label such as (a), (b), (c) or (1), (2), (3).

(c) A "Remark" or "Observation" environment for standalone points in a theoretical section.

The reason for this rule: unordered bullet points signal informality. They fragment the argument into disconnected pieces and make it easy to hide logical gaps. Ordered enumeration forces the writer to consider the sequence and relationship between items.

Italicized labels without ordering markers (e.g., "*Label noise:*" and "*Mechanism impurity*" as standalone items) are a borderline violation. Convert to (a)/(b) or (i)/(ii).

### 2.3 Symbol and Notation Discipline

Every mathematical symbol must be formally introduced before its first use. "Let $K$ denote the number of domains" must precede any equation or sentence that uses $K$. This applies to all single-letter variables without exception.

Specific requirements:

(a) Greek letters: State what each one represents on first use. "$\sigma_{\min}$" is meaningless until you write "where $\sigma_{\min}$ denotes the smallest singular value of the basis matrix $\mathbf{B}$."

(b) Subscripts and superscripts: Define the indexing convention. If $i$ indexes data points and $k$ indexes domains, state this once in the notation section or at first use, and never swap them.

(c) Bold vs. non-bold: Be consistent. If vectors are bold ($\mathbf{z}$) and scalars are not ($z$), maintain this throughout. Mixing conventions within a single document is a serious error.

(d) Operator notation: If you use $\|\cdot\|$ for a norm, specify which norm (e.g., "$\|\cdot\|_2$ denotes the Euclidean norm").

(e) Reusing symbols: Never reuse a symbol for two different purposes in the same document. If $T$ is the number of time steps, it cannot also be a transformation matrix.

(f) Introduce-and-discard: Do not introduce a new variable (e.g., $s$) only to equate it immediately to an existing one ($K_{\text{active}}$) and never use it again. Write "only $K_{\text{active}}$ entries are nonzero" instead of "is $s$-sparse (only $s = K_{\text{active}}$ mechanisms are active)."

### 2.4 Term Definition Protocol

Every technical term or coined phrase must be explicitly defined at its first occurrence. This includes:

(a) Novel terms introduced by the paper: "We define *mechanism trajectory* as the continuous path $\alpha(t)$ through the space of mixing coefficients."

(b) Terms borrowed from adjacent fields that the expected audience may not know: If you use "sufficient variability" from the nonlinear ICA literature, provide a one-sentence gloss and a citation.

(c) Abbreviations: Spell out on first use, then use the abbreviation consistently. "Causal Representation Learning (CRL)" becomes "CRL" for all subsequent occurrences. Never re-expand after the first definition unless starting a new major document. Common abbreviations that may not be known to all reviewers (DGP, OOD, SNR, QA, pp) must also be expanded on first use.

### 2.5 Figure and Table References

Every reference to a figure or table must specify its location. This means:

(a) In a paper: "as shown in Figure 3 (left panel)" or "see Table 2, column 3". Never write "as shown in the figure" or "see the table below" because reviewers may be reading a differently-paginated version.

(b) Cross-referencing: When prose references a specific table entry, cite the row and column where helpful: "the MCC score of 0.984 reported in Table 1, row 'Ours', column 'd=64'."

(c) Visual changes require a cross-reference audit. After changing a figure or table, verify every caption, accessibility description, panel reference, and claim in the surrounding prose. Cosmetic changes still require confirming that the semantics did not change. For the full audit, follow §3.8.

### 2.6 Inline Labels Are Section-Specific

The `\textbf{X.}` or `\paragraph{X.}` style inline label (e.g., `\textbf{Setup.} We use ...`) is standard in:

(a) Experimental Setup paragraphs (b) Component descriptions inside the Method section (c) Appendix subsections with parallel structure (d) Practitioner notes / engineering findings sections

It is **forbidden** in:

(a) Introduction prose (b) Related Work prose (c) Conclusion prose (d) Limitations narrative (e) Abstract

In these prose-flow sections, inline labels disguise bullet points as paragraphs, fragmenting the argument and signaling informality. The narrative should flow as continuous prose with topic sentences carrying the structure.

Lint check: any `\textbf{X.}` appearing inside Introduction / Related Work / Conclusion paragraphs is a red flag. If two ideas need to be marked off, restructure into two separate paragraphs whose topic sentences carry the contrast.

---

## 3. Paper Writing Logic

### 3.0 Section-Level Blueprinting (Overarching Principle)

Before writing any section, produce a **sentence-level blueprint** that specifies the role of each sentence or sentence group. A blueprint is a short ordered list such as:

(a) Related Work: paradigm → limitation → our distinction (b) Introduction: broad motivation → specific gap → prior attempts and their shortcomings → our approach → contributions list (c) Method: problem setup → intuition/overview → component 1 → component 2 → full algorithm (d) Experiments: research questions → setup → results by question → ablations → limitations

Within each blueprint slot, further specify the approximate number of sentences. For example, a Related Work paragraph blueprint might read:

  S1--S3: Define the paradigm and cite foundational work. S4--S5: Expand two representative learning-based methods with limitations. S6: Group remaining works by shared limitation with merged citations. S7: Distinguish our approach.

This blueprint should be drafted (mentally or in comments) before any prose is written. It prevents two failure modes: (a) sections that meander without clear argumentative progression, and (b) sections where paragraph lengths are wildly unbalanced because the writer did not plan how much space each point deserves.

When revising, check the existing text against its blueprint. If a sentence does not clearly serve one of the blueprint slots, it is either misplaced or unnecessary.

### 3.1 Abstract

The abstract follows a rigid four-part structure in roughly 150 to 250 words:

(1) **Problem**: One or two sentences establishing the research gap. Be specific about what is missing, not about what exists.

(2) **Approach**: Two to three sentences describing the proposed method at a conceptual level. Name the method. State the key idea that distinguishes it from prior work.

(3) **Theory/Guarantee**: One sentence on the theoretical contribution, if any. State what is proved and under what conditions.

(4) **Results**: One to two sentences on empirical findings. Include at least one concrete number.

### 3.2 Introduction

The introduction expands the abstract into roughly 1.5 pages. It follows a funnel structure with a sentence-level blueprint for each paragraph:

**P1: Vision and Background** (broad motivation → narrow the scope) S1--S2: Broad area and recent progress. S3--S4: Narrow to the specific capability gap your work addresses.

**P2: The Problem with the Status Quo** (what exists → why it fails) S1: State the prevailing approach. S2--S3: Present empirical or logical evidence that it is insufficient. S4: Optionally state a hypothesis for *why* it fails.

**P3: Why Existing Solutions Fall Short** (prior attempts → their limitations) S1: Acknowledge recent attempts to solve the problem, with citations. S2--S3: Identify the fundamental limitation shared by these attempts. Cite concurrent work here if relevant.

**P4: Our Approach** (key idea → how it works) S1: "We propose [method name], which addresses [the bottlenecks named in P3]." S2--S4: Describe the two or three core design decisions at a conceptual level. Each design decision should map to one limitation identified in P3.

**P5: Contributions** (explicit ordered list) Use "(i) We propose..., (ii) We demonstrate..., (iii) We achieve..." format. Each contribution should be concrete and verifiable, not vague. Include at least one number in the empirical contribution.

### 3.3 Method Section

The method section must be self-contained: a reader should be able to reimplement the method from this section alone (plus the appendix for proof details).

**P1: Problem Setup** S1--S2: Formally define the input, output, and objective. S3--S4: Introduce all notation. Every symbol must appear here before it is used later.

**P2: Method Overview** S1: One-sentence summary of the full pipeline. S2--S4: Name each component and state its role in one sentence each. This paragraph serves as a roadmap so the reader knows what is coming before the details.

**P3--P_n: Component Details** (~1 subsection per component) For each component, follow: intuition (why this component is needed, 1--2 sentences) → formal definition (equations, algorithms) → design choices and justification (why this design over alternatives, 1--2 sentences).

**Final: Full Algorithm** (pseudocode or formal procedure) Summarize the entire pipeline as Algorithm 1 so the reader can see how the components fit together.

### 3.4 Experiments Section

**P1: Research Questions** (1--3 sentences) Explicitly state the RQs the experiments will answer. Number them: "We aim to answer: (1) Does \method improve...? (2) How does each component contribute...? (3) Do the results transfer...?"

**P2: Setup** S1--S2: Datasets and benchmarks (with citations and sizes). S3: Baselines (name each, one sentence explaining why it is a fair comparison). See §4.4 for baseline naming conventions. S4: Metrics (define any non-standard metric). S5: Key hyperparameters and compute budget.

**P3--P_n: Results by Research Question** For each RQ: state the finding in one topic sentence → present the supporting table or figure → provide a takeaway sentence explaining *why* the result holds (not just *what* the numbers are). Organize by research question, not by dataset.

**Ablations** Isolate the contribution of each component by removing it. Each ablation row in the table needs a one-sentence interpretation.

**Limitations** (1--2 sentences, honest) State what the experiments do not cover and why. This preempts reviewer criticism and signals maturity.

### 3.5 Related Work

Related work is not a literature dump. It is a structured argument showing why existing work is insufficient and why your contribution is necessary.

#### 3.5.1 Macro Structure

Organize by *conceptual themes*, not by chronology or by individual paper. Each `\paragraph{}` covers one theme (e.g., "Agent skills" and "Self-evolving agents"). Aim for roughly balanced paragraph lengths; if one paragraph is twice the length of another, restructure.

#### 3.5.2 The "Expand-Two, Group-the-Rest" Pattern

A common and effective strategy for covering a large body of related work concisely:

(a) **Pick two representative papers to expand** (1--2 sentences each, describing method and limitation).

(b) **Group the remaining papers by shared limitation** and cite them together in a single sentence. For example: "Voyager~\citep{A}, Yunjue~\citep{B}, and TTE~\citep{C} all synthesize atomic tool functions; none, however, can construct the interdependent multi-file structure a full skill package demands." This is far more effective than describing each paper individually with its own limitation sentence.

(c) When multiple papers share the same limitation, **merge citations into one clause** rather than writing separate "X does A; however, B" sentences for each. Bad: three consecutive sentences each ending with "however, it cannot handle multi-file packages." Good: one sentence citing all three, followed by the shared limitation once.

#### 3.5.3 Sentence Variety

Never use the same "method + however + limitation" template for consecutive papers. Alternate between:

(a) Concessive clauses: "While X achieves ..., the resulting skills are ..." (b) Contrast: "Unlike X which ..., Y takes a different route by ..." (c) Concession: "Although X demonstrates ..., it relies on ..." (d) Group + summary: "A, B, and C all produce ...; none, however, can ..."

#### 3.5.4 Do Not Announce Structure

Do not write meta-structural sentences like "existing methods exhibit three recurring limitations" or use transitions like "On the first front." These read like presentation slides, not research prose. Instead, let the reader discover the structure through the argument itself. A sentence like "Moving beyond atomic tool generation, several methods distill higher-level behavioral knowledge" is acceptable because it describes *content*, not *structure*.

#### 3.5.5 Closing Sentences Across Paragraphs

Each paragraph should end by distinguishing your approach, but the closing sentences of different paragraphs must emphasize *different aspects* of your contribution. If one paragraph closes by highlighting your generation mechanism (e.g., "iterative co-evolution of multi-file packages"), the other should highlight a different design choice (e.g., "information isolation to prevent confirmation bias"). Repeating the same distinction verbatim across paragraphs signals shallow writing.

#### 3.5.6 Concurrent and Closely Named Work

(a) If a concurrent work shares a similar name or scope, mark it explicitly: "the concurrent work X~\citep{...}" on first mention.

(b) Ensure \citep{} keys are consistent across the entire paper (introduction, related work, experiments). Duplicate BibTeX entries with different keys for the same paper will cause the reference to appear twice in the bibliography.

#### 3.5.7 Recurring Phrases

Key distinguishing phrases (e.g., "structured multi-file skill packages") should appear at most twice in the entire Related Work section. Overuse dilutes their impact and makes the prose feel templated.

### 3.6 Conclusion Section Blueprint

The conclusion is the shortest substantive section: 3 to 5 sentences in a single paragraph (or two short paragraphs at most). It is not a summary of the paper; it is a distilled statement of the contribution and its scope.

**S1: What we did.** One sentence defining the method with its core mechanism, not its full description. ("We presented X, a Y that does Z.")

**S2-S3: Headline results.** The two or three most important numerical findings, stated as comparisons against the most relevant baselines. Do not enumerate every table.

**S4 (optional): Analysis trace.** One sentence pointing to *why* the method works, with cross-references to the analysis sections that establish it.

**S5: Future-work hedge.** One sentence stating the scope of validation and what is left for future work.

**Forbidden in Conclusion:**

(a) Repetition of mechanism details from the Method section. (b) Recitation of all numerical results from the Experiments section. (c) Future-work claims that duplicate a "Broader Applicability" or analogous body section's content. The hedge belongs in one place; the other should be a single referential sentence or omitted. (d) Stand-alone restatements of the contribution list from the Introduction.

A confident Conclusion is short. An expanding Conclusion is often a sign of insecurity about the contribution.

### 3.7 Three-Layer Information Separation in Tables

Tables convey information across three layers — table headers, caption, and surrounding prose — and each layer has a distinct role. Information that appears in one layer must not be repeated in another.

**Table headers** carry column names and units (where short enough to fit, e.g., "Cor. (%)", "Time (h)").

**Caption** carries:

(a) A topic phrase: what this table measures and on which model/benchmark. (b) Definitions for any variants or column names that cannot fit in the header (e.g., "First keeps the first valid triplet; Min takes the minimum"). (c) The base of relative numbers (e.g., "Time is wall-clock training cost relative to First"). (d) Caveats specific to this table.

The caption does NOT carry:

(a) Re-explanation of self-evident column names ("Cor. is correctness (%)" when the header already says "Cor. (%)"). (b) Restatement of the experimental setup already in the Setup section (e.g., the sample size N that already appears in every table need not be repeated). (c) Headline results — those belong in the prose.

**Prose** carries mechanism and interpretation. It must NOT re-cite every cell value from the table; readers see the table. Reference specific numbers only when making a sharp comparison ("Method A drops accuracy by Δ pp", not "Method A scores N1, Method B scores N2, Method C scores N3 ..."). The prose's job is to explain WHY the numbers fall the way they do.

Typical failure mode: a paragraph following a 5-row table that recites all 5 rows in sentence form, then ends with "the canonical X variant is best." This is information-equivalent to the table and adds zero analytical value.

### 3.8 Figure and Table Design and Audit

Whenever a task creates, converts, revises, or reviews a figure, plot, or table, read [Figure and Table Review Standard](references/figure-table-review.md) in full before acting. This reference is mandatory even when the requested change appears cosmetic, because spacing and icon edits can change the apparent semantics or make a caption stale.

Apply four gates in order: (1) choose the correct representation, (2) preserve the intended claim and visual hierarchy, (3) verify geometry and legibility at the final paper size, and (4) synchronize the visual with its caption, accessibility description, surrounding prose, and source data. A standalone high-resolution render is not sufficient. Compile the paper and inspect the rendered page at its actual placement size before declaring the work complete.

---

## 4. Language and Style

### 4.1 Sentence Construction

(a) Prefer active voice for claims about the paper's contributions: "We prove that..." not "It is proved that..."

(b) Use passive voice sparingly, only when the agent is genuinely irrelevant: "The model is trained for 100 epochs" is acceptable.

(c) Keep sentences under 35 words when possible. Long sentences in academic writing usually indicate that two ideas have been fused into one.

(d) Avoid parenthetical asides that span more than 5 words. If the aside is important enough to include, it deserves its own sentence.

(e) Avoid filler words: "itself," "actually," "basically," "essentially." If removing the word does not change the meaning, remove it.

### 4.2 Word Choice

(a) Prefer precise verbs over vague ones: "achieves" over "gets", "demonstrates" over "shows", "requires" over "needs".

(b) Avoid informal intensifiers: "very", "really", "quite", "extremely". In academic writing, intensity comes from data, not adverbs.

(c) Avoid redundant phrasing: "in order to" becomes "to"; "due to the fact that" becomes "because"; "a total of 5 experiments" becomes "5 experiments".

(d) Do not use contractions in formal academic text.

(e) Use "approximately" instead of "~" in prose. The tilde is acceptable in tables and inline with numbers in parentheses, but not in running text.

### 4.3 Paragraph Transitions

Every paragraph must connect to the preceding one. Use explicit logical connectors: "In contrast to the discrete formulation above, we now consider...", "Building on Theorem 4.1, we derive...", "While the above addresses identifiability, we now turn to estimation error."

Avoid generic transitions like "Next, we discuss..." or "In this section, we present..." These tell the reader nothing about the logical relationship between paragraphs.

### 4.4 Naming Conventions for Baselines and Methods

Baseline and method names are proper nouns. Once defined, their capitalization, spelling, and form are fixed across the entire paper — including section bodies, table headers, captions, figure labels, and appendices.

(a) **First introduction**: define with the descriptor explicitly: "Raw (unmodified generation)" / "FoRAG (PPO with subclaim-verified sentence reward)" / "Our method, CorVer (Corpus Verify), ..."

(b) **Subsequent use**: the bare name, no article, no descriptor:

  ✅ "CorVer improves over Raw on every cell." ❌ "Our method improves over the raw baseline on every cell."

(c) **Capitalization stability**: lowercase forms ("raw", "corver") in body text introduce inconsistency and signal carelessness. Stick to the defined form everywhere.

(d) **Abbreviations of method names**: avoid abbreviating your own method name ("we abbreviate CorVer as CV") — it adds nothing and risks collision with other acronyms.

---

## 5. Cross-Section Workflows

Certain editing tasks span multiple sections and require coordinated changes. The recipes below prevent the most common slip-ups.

### 5.1 Story Framing Drift Audit

When any major section's framing changes (e.g., the Introduction's central narrative is rewritten), residual phrasings of the old framing typically survive in the Abstract, Conclusion, and Appendix sections. These create cross-section inconsistency that reviewers notice immediately.

**Recipe** after rewriting any framing:

(a) Extract 2--3 keywords or phrases unique to the old framing (e.g., "decoupling density from cost", "cost decoupling").

(b) Run `grep -rn` across all `.tex` files for each keyword.

(c) For each hit, classify: (i) update to new framing, (ii) keep as neutral reference, or (iii) delete as redundant.

(d) Pay extra attention to: section/paragraph headers, table captions, keyfinding boxes — these are easy to forget.

### 5.2 Appendix ↔ Main Text Migration Recipe

When promoting content from the appendix to the main text (or pushing main-text content into the appendix), follow this order:

(1) **Insert** the new version at the destination with a new label (`sec:xxx` for main text, `app:xxx` for appendix).

(2) **Trim** the source location. If a table is moved, the source must drop the table entirely to avoid a duplicate-label warning. Mechanism prose / proofs / case studies typically stay in the appendix while the topline result moves to main text.

(3) **Update cross-references**: run `grep -rn "old_label"` to find every `\ref{old_label}`. Classify each:

  (a) Now refers to main text → update to `\ref{sec:xxx}` (b) Still refers to appendix mechanism → keep as `\ref{app:xxx}` (c) Both → cite both: "compared in \S\ref{sec:xxx} (mechanism in Appendix~\ref{app:xxx})"

(4) **Verify** no stale references remain if the source label is deleted (would produce `??` in the rendered PDF).

### 5.3 Restructuring Appendix Section Levels

If the appendix uses a single outer `\section` wrapper with nested subsections / subsubsections, every section renders as A.1, A.2, A.1.1, etc. To produce top-level A, B, C, D sections instead:

(1) Delete the outer `\section{...}` wrapper (and its label, if unreferenced).

(2) Promote all `\subsection{` → `\section{` (these become A, B, C, ...).

(3) Promote all `\subsubsection{` → `\subsection{` (these become A.1, A.2, ...).

(4) **Order matters**: do step (2) BEFORE step (3) to avoid cross-contamination — promoting subsection first leaves subsubsection untouched, but doing the reverse would re-promote the newly created subsections.

(5) Before deleting the outer wrapper, verify its label is not referenced elsewhere.

### 5.4 Trust-but-Verify Supervisor Feedback

Feedback from senior collaborators is high-signal but not infallible. Two specific red flags worth pushing back on:

(a) **Overclaiming language**: Requests to add "novel", "first", "state-of-the-art", or unbacked quantitative adjectives without commensurate evidence. These claims invite reviewer scrutiny that the paper may not be ready for. Apply the intent (e.g., "lead with what we propose") without inheriting the risk.

(b) **Hiding building-block citations**: Requests to remove citations of borrowed components under the framing "this hides our contribution". Building- block citations are honest scholarship; hiding them backfires when a reviewer notices the omission. Restructure to lead with the contribution while keeping the citations in supporting positions.

(c) **Inline labels in narrative sections**: Requests to add `\textbf{X.}` style labels in Introduction or Related Work to "make the structure clearer". See §2.6 — this is forbidden in narrative sections.

When pushing back, do so with a concrete reason (e.g., "We only measured end-to-end wall clock, not per-call latency, so 'orders of magnitude' is unbacked"), not abstract disagreement.

---

## 6. Anonymous Submission Checklist

For double-blind venues (ACL/EMNLP/NeurIPS/ICML/ICLR/etc.), the rendered PDF must not contain identifying information. The source code may also need to be clean if the venue collects supplementary materials.

### 6.1 PDF-Visible Checks (Mandatory)

(a) **Author block**: replaced with "Anonymous Authors" or venue-specific placeholder.

(b) **Acknowledgments section**: removed (preferred) or commented out in source with a `% re-enable for camera-ready` reminder.

(c) **Emails, affiliations, personal URLs**: none in main text, footnotes, or captions.

(d) **Code link**: use `anonymous.4open.science` (the standard anonymous code hosting for ML venues) with a footnote on the first mention of the method name in the Introduction:

  ```
  We propose \textbf{Method}\footnote{Code: \url{https://anonymous.4open.science/r/Method-XXXX}.} ...
  ```

(e) **Figure filenames and captions**: generic names (`scaling_heatmap.pdf`, not `my-lab-scaling.pdf`); no author paths in caption text.

(f) **Bibliography**: cite only published work; do not cite "(Anonymous, In preparation)" entries that reveal the scope of an unpublished pipeline.

### 6.2 Source-File Checks (Strict Venues / Future-Proofing)

Some venues collect source `.tex` files. Even when they do not, cleaning the source costs nothing and protects against accidental leak via supplementary upload.

(a) Run `grep -rn "<your-name>\|<lab-name>" --include="*.tex"` — should return nothing.

(b) LaTeX `% comments` should not name authors, collaborators, or advisors.

(c) Macro definitions: `\newcommand{\yourname}{...}` that hardcode names are visible in source. Remove or rename to generic placeholders before submission.

(d) Plot scripts (`figure/*.py`): no `/Users/yourname/` absolute paths or user-specific config.

### 6.3 The Two Modes

(a) **Strict mode** (default): PDF clean only. Sufficient for most ACL/EMNLP/NeurIPS submissions; reviewers see only the PDF.

(b) **Paranoid mode**: PDF + source clean. Required when the venue collects `.tex` source or when source is uploaded as supplementary material. Spend an extra 10 minutes on §6.2 checks.

---

## 7. Pre-Submission Checklist

Before finalizing any academic text, verify the following:

(1) Every symbol is defined before first use. (2) Every technical term is defined at first occurrence. (3) Every figure and table reference includes a location specifier. (4) No em dashes, en dashes (in prose), or unordered bullet points appear anywhere. (5) All numbers are internally consistent across sections. (6) Every claim is supported by a citation, a theorem, or experimental evidence. (7) The abstract, introduction, method, and conclusion tell a coherent and non-contradictory story. (8) Prose claims immediately following a table match the table's numbers exactly. (9) Empirical observations are not stated with the certainty of proved theorems. (10) No variable is introduced solely to be equated to another and never reused. (11) Every experiment has an explicit takeaway sentence, not just numbers. (12) No reference to appendix/supplement without also inlining the key idea. (13) Story framing audit: grep for keywords from any abandoned framings; verify no residual mentions in Abstract, Conclusion, or Appendix (§5.1). (14) Anonymity audit (if applicable): no author/affiliation in PDF; for strict venues, no identifying strings in `.tex` source or macro definitions (§6). (15) Conclusion does not duplicate hedges or future-work claims already made in a "Broader Applicability" or analogous body section (§3.6). (16) Quantitative adjectives ("orders of magnitude", "millisecond-scale", etc.) in Introduction/Abstract are backed by a measurement section in the body (§1.7). (17) Baseline and method names use consistent capitalization throughout — no lowercase variants of established proper nouns (§4.4). (18) No `\textbf{X.}` inline labels appear inside Introduction, Related Work, Conclusion, or Limitations prose (§2.6). (19) Tables, captions, and surrounding prose do not duplicate the same information across layers (§3.7). (20) Every figure or table has one explicit communicative job, and its visual hierarchy reflects the paper's contribution priorities (§3.8). (21) No icon, arrow, border, label, or data mark is clipped, overlapped, ambiguous, or touching another element at final paper size (§3.8). (22) Text remains legible in the compiled paper without zooming, and every label has visible padding from its container (§3.8). (23) Tables are used for exact lookup, figures for patterns or relationships, and prose for short text-only inventories; no artifact is retained merely because it already exists (§3.8). (24) Tables do not place unrelated grouping schemes side by side or retain numbers that support no claim (§3.8). (25) Figure and table colors, symbols, names, units, counts, and ordering agree with the source data and the rest of the paper (§3.8). (26) Captions, accessibility descriptions, and all textual references have been re-audited after the final visual revision (§2.5, §3.8). (27) Both standalone assets and the compiled paper page have been rendered and visually inspected after the last meaningful change (§3.8).
