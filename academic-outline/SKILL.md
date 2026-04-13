# Academic Outline Skill

When the user asks for an academic outline, follow these steps:

1. **Identify the document type** from the user's request (conference paper, workshop paper, proposal/grant, thesis chapter). If unclear, ask.
2. **Identify the page limit or venue** if mentioned (e.g., "8-page NeurIPS paper", "4-page workshop", "NSF proposal"). This determines scale.
3. **Ask the user for a 2-3 sentence summary** of their work: what problem, what method, what result. If already provided in conversation, use it directly.
4. **Generate the outline** following the templates below, adapting sentence counts and section presence to the document type and page limit.

------

## Output Format

The outline should be a structured markdown document. For each section and subsection:

- State the **purpose** of that section in one line
- State the **approximate sentence count** or paragraph count
- Describe the **logical flow** as a chain: `point A -> point B -> point C`
- Where applicable, note what to cite or reference

Do NOT write the actual paper content. Only provide structural and logical guidance.

------

## Template: Conference Paper (8-10 pages)

### Title

- Should contain: method name (if any) + task/problem + key differentiator
- 1 sentence, under 15 words preferred

### Abstract (~150-200 words, ~8-10 sentences)

- Flow: `problem significance (1-2 sentences) -> existing approaches and their limitation (2 sentences) -> our key idea in one line (1 sentence) -> method summary (2-3 sentences) -> key results with numbers (1-2 sentences)`
- Must contain at least one concrete quantitative result

### 1. Introduction (~1-1.2 pages, ~18-25 sentences)

- **Para 1 (3-4 sentences):** Big picture motivation. Why does this problem matter? Connect to a broad audience.
  - Flow: `broad context -> specific problem -> why it matters`
- **Para 2 (4-5 sentences):** Prior work at a high level and their limitations.
  - Flow: `existing paradigm -> what they do well -> critical weakness or gap`
- **Para 3 (3-4 sentences):** Key insight or observation that motivates your approach.
  - Flow: `observation/intuition -> why this hasn't been explored -> what it enables`
- **Para 4 (4-5 sentences):** Your method summary.
  - Flow: `we propose X -> X works by doing Y -> key design choices -> how it addresses the gap`
- **Para 5 (3-4 sentences):** Results highlights and contributions.
  - Flow: `experimental setup in one line -> headline result -> secondary results`
- **Contributions list (3-4 bullet points):** Each bullet is one sentence. Cover: (1) problem formulation or insight, (2) method, (3) empirical results, (4) optional: analysis/resource release.

### 2. Related Work (~0.75-1 page, ~15-20 sentences)

- Organize into 2-4 topical subsections (not a flat list)
- Each subsection: 4-6 sentences
- Flow per subsection: `define the line of work -> summarize key papers (2-3) -> state how our work differs`
- Final paragraph (2-3 sentences): position your work relative to the closest prior work
- Tip: can also be placed after experiments depending on venue convention

### 3. Preliminaries / Problem Setup (~0.5-0.75 pages, optional)

- Include if: formal problem definition, background notation, or assumptions needed
- ~8-12 sentences
- Flow: `notation setup -> formal problem definition -> key assumptions -> what we aim to learn/optimize`

### 4. Method (~2-2.5 pages, ~35-50 sentences)

- **4.1 Overview (4-6 sentences):** High-level pipeline description. A reader should get the full picture from this subsection alone.
  - Flow: `input -> key steps -> output`
- **4.2-4.4 Method components (one subsection per major component):**
  - Each subsection: 8-15 sentences
  - Flow per component: `what this component does -> formulation/equation -> design choices and why -> connection to the next component`
- **4.X Training / Optimization (5-8 sentences):**
  - Flow: `loss function -> optimization procedure -> any tricks or schedules`
- Include a method figure reference early in Section 4.1
- Equations should be referenced in text, not left floating

### 5. Experiments (~2.5-3 pages)

This is the most structured section. Follow this organization:

- **5.1 Experimental Setup (8-12 sentences)**
  - Datasets: name, size, why chosen (3-4 sentences)
  - Baselines: list with 1-sentence description each (4-6 sentences)
  - Metrics: which ones and why (2-3 sentences)
  - Implementation details: defer to appendix but state key hyperparameters (2-3 sentences)
- **5.2 Main Results (10-15 sentences)**
  - One main comparison table or figure
  - Flow: `overall trend (1-2 sentences) -> best result highlighted (1-2 sentences) -> comparison to strongest baseline (2-3 sentences) -> discussion of when/where method wins or loses (3-4 sentences) -> takeaway (1-2 sentences)`
- **5.3 Ablation Study (8-12 sentences)**
  - One ablation table
  - Test each major design choice by removing/replacing it
  - Flow: `what we ablate and why -> results -> which component matters most -> interpretation`
- **5.4 Analysis (8-15 sentences, 1-3 subsections)**
  - Pick 2-3 of the following based on what strengthens the paper:
    - Sensitivity analysis (hyperparameters, data size)
    - Qualitative examples / case studies / visualizations
    - Computational cost comparison
    - Failure case analysis
    - Scaling behavior
  - Each analysis block: `question we ask -> setup -> result -> insight`

### 6. Conclusion (~0.5 page, ~6-8 sentences)

- Flow: `restate problem and why it matters (1-2 sentences) -> summarize method and key idea (2 sentences) -> main empirical takeaway (1-2 sentences) -> limitations and future work (2-3 sentences)`
- Never introduce new results here

### Appendix (no page limit usually)

- Implementation details, full hyperparameter tables
- Additional experiments, full ablations
- Proofs (if any)
- Dataset details, licenses, broader impact

------

## Template: Workshop Paper (4 pages)

Scale down the conference template:

- **Abstract:** 100-120 words, 6-7 sentences
- **Introduction:** 12-16 sentences, merge motivation and related work; skip separate related work section
- **Method:** 1-1.5 pages, 20-30 sentences, fewer subsections (2-3)
- **Experiments:** 1-1.5 pages
  - Setup: 5-7 sentences
  - Main results: 8-10 sentences (1 table)
  - One ablation or analysis: 5-8 sentences
- **Conclusion:** 4-5 sentences
- No appendix (usually)

------

## Template: Research Proposal / Grant

Structure varies by venue (NSF, internal, PhD proposal). General skeleton:

- **Project Summary / Abstract (~250 words, 12-15 sentences)**
  - Flow: `problem and significance -> proposed approach -> expected outcomes and impact`
- **Introduction and Motivation (1-2 pages)**
  - Heavier on "why this matters" than a paper; emphasize impact, timeliness, and gap
  - ~25-35 sentences
  - Flow: `societal/scientific significance -> state of the art -> gap -> our vision`
- **Background and Related Work (1-1.5 pages)**
  - More thorough than a paper; demonstrate expertise
  - ~20-25 sentences
- **Proposed Research (2-4 pages, core section)**
  - Organize by aims/thrusts (typically 2-4)
  - Each aim: ~15-20 sentences
    - Flow: `research question -> approach -> preliminary evidence (if any) -> expected outcome -> risk mitigation`
  - Include a timeline or milestones subsection
- **Preliminary Results (0.5-1 page, if available)**
  - Show feasibility, not completeness
  - ~10-15 sentences
- **Broader Impact / Intellectual Merit (0.5 page)**
  - ~8-10 sentences
- **References:** generous, show breadth

------

## Template: Thesis Chapter

A thesis chapter is typically a paper expanded with more context:

- **Add** a longer literature review (2-4 pages, organized thematically)
- **Expand** method section with more intuition, derivations, proofs
- **Expand** experiments with all results (nothing in appendix, put everything inline)
- **Add** a "Discussion" section (0.5-1 page) between Experiments and Conclusion
  - Flow: `what did we learn -> connections to broader theory -> limitations in depth -> open questions`
- Sentence counts scale ~1.5-2x from the conference paper template

------

## Adapting the Outline

After generating the base outline, tailor it:

- If the user provides their specific contributions, map each contribution to where it appears in the outline
- If the user mentions specific baselines or datasets, slot them into Section 5.1
- If the paper is more theoretical (proofs, theorems), expand Section 3 (Preliminaries) and add a "Theoretical Analysis" section before experiments
- If the paper is empirical-heavy, expand Section 5 and keep Section 4 concise
- If the paper has no experiments (pure theory, position paper), replace Section 5 with "Theoretical Results" or "Discussion"

------

## Checklist (present at the end of every outline)

After the outline, provide a short checklist:

-  Does the introduction clearly state the gap?
-  Is each contribution backed by an experiment or analysis?
-  Does Section 5.2 directly support the claims in the abstract?
-  Are ablations testing meaningful design choices?
-  Is the method figure referenced and informative?
-  Does related work position (not just list) prior work?