---
name: survey-writing
description: >
  Design and write survey, review, state-of-the-art, and systematization-of-knowledge papers in ML, AI, and adjacent technical fields. Use for taxonomy design, literature synthesis, comparative analysis, open problems, survey introductions, thematic related work, and full survey manuscripts. Trigger on survey paper, review paper, literature review, SoK, position paper with broad literature synthesis, or 综述. Use academic-writing for general prose conventions and academic-self-check for the final audit.
---

# Survey Writing

A survey must reveal structure that is difficult to see from individual papers. Organize the field, compare approaches, expose assumptions, and derive research questions. Do not produce a paper-by-paper bibliography in prose.

## Before Drafting

Establish:

1. the topic, time range, venues, and inclusion criteria;
2. the paper corpus and how it was collected;
3. the intended audience;
4. the central questions the survey will answer;
5. the taxonomy axes and canonical terminology;
6. the target venue and length.

Read the relevant papers before drafting synthesis. Do not infer a taxonomy from titles and abstracts alone. If the corpus or scope is incomplete, state the assumption and avoid claims of comprehensive coverage.

## Core Workflow

### 1. Distill each paper

Record only dimensions that support comparison:

| Dimension | Example |
| --- | --- |
| problem | what question the work answers |
| assumptions | data, supervision, access, or environment required |
| mechanism | the central technical idea |
| evidence | theory, datasets, benchmarks, or deployment |
| limitation | boundary relevant to the taxonomy |

Do not draft prose during extraction.

### 2. Design the taxonomy

Choose axes that represent consequential design decisions, assumptions, or goals. Test three properties:

1. **coverage:** every in-scope work has a defensible place;
2. **discrimination:** meaningfully different approaches do not collapse into one cell;
3. **clarity:** category boundaries can be stated without a list of exceptions.

Allow explicit hybrid or multi-label placement when the field genuinely overlaps. Do not force a tree if a matrix or layered map fits better.

Load [survey-architecture.md](references/survey-architecture.md) when planning the full paper or a taxonomy figure.

### 3. Write claims before citations

Organize each body paragraph around a shared pattern, tension, or progression. A useful structure is:

1. state the shared idea;
2. use representative works as evidence;
3. compare how they differ;
4. assess the collective strength or limitation.

Group papers that play the same evidentiary role. Expand only works whose technical difference matters to the reader. If several papers are too heterogeneous for one claim, do not hide them under “other approaches.”

Load [synthesis-and-citations.md](references/synthesis-and-citations.md) when writing the main body, related work, or bibliography.

### 4. Derive cross-cutting analysis

The discussion must contain observations that require the survey corpus:

1. assumptions shared across categories;
2. combinations the literature rarely explores;
3. evaluation practices that distort comparison;
4. gaps between theory and deployment;
5. scalability or data regimes that remain untested;
6. terminology that differs across communities.

Support frequency claims with counts from the corpus. Present preferences as evidence-based tradeoffs rather than the survey authors' taste.

### 5. Make future directions actionable

Tie every direction to a gap already demonstrated. Explain why the gap matters and identify a concrete obstacle, missing resource, or plausible technical route. Prefer four developed directions over a long wish list.

## Survey Voice

Use the authorial “we” for the survey's actions, such as organizing, comparing, or identifying. Describe surveyed work neutrally. State consensus only when the corpus supports it.

Prefer comparison:

> Both families seek invariant representations, but they differ in what supplies the invariance signal.

Avoid sequence:

> Paper A uses labels. Paper B uses interventions. Paper C uses time.

Map synonyms on first use and choose one canonical term thereafter. Use a terminology table when variation itself is a contribution.

## Visual Evidence

Use:

1. a taxonomy figure when the organization is a primary contribution;
2. a comparison table when readers need repeated property lookup;
3. a timeline only when temporal development explains the field;
4. quantitative corpus plots only when counts are reproducible from the selected corpus.

Order table rows by taxonomy or analytical logic, not automatically by year or alphabet. Explain the pattern in prose rather than narrating cells.

## Section-Level Requests

When asked to write one section, inspect or request the scope, taxonomy branch, included papers, terminology, adjacent sections, and target length. State unresolved assumptions outside the manuscript text. Connect the opening and closing to adjacent sections without repeating their content.

## Common Failure Modes

Load [survey-antipatterns.md](references/survey-antipatterns.md) when prose becomes repetitive or paper-by-paper.

In particular, reject:

1. a topic sentence followed by independent paper summaries;
2. citation dumps at the end of a paragraph;
3. taxonomies based on superficial implementation details;
4. future directions disconnected from the main analysis;
5. selective performance numbers that make the survey look promotional;
6. conclusions that merely repeat the abstract.

## Completion

Apply the general prose and visual rules from `academic-writing`. Then invoke `academic-self-check` for claims, citation metadata, cross-section consistency, and rendered layout. Do not maintain a second full submission checklist here.
