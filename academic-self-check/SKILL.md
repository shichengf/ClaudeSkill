---
name: academic-self-check
description: >
  Audit a completed or near-complete academic manuscript for unsupported claims, numerical drift, terminology and notation inconsistencies, citation problems, figure and table defects, LaTeX layout issues, anonymity risks, and submission readiness. Use after drafting, after a major result or figure update, before committing a paper revision, or when the user asks for a full-paper review, final check, consistency audit, or reviewer-style inspection. This skill diagnoses first and edits only when the user authorizes edits.
---

# Academic Self-Check

Audit the paper independently from the drafting process. The goal is to find defects that a familiar author stops seeing, not to rewrite correct prose for stylistic novelty.

## Select the Mode

Use **report-only mode** when the user asks to review, inspect, check, diagnose, or assess. Do not modify files.

Use **fix mode** when the user asks to correct, revise, clean, or apply the findings. Preserve valid content and unrelated local changes. For judgment calls, explain the tradeoff before making a material rewrite.

If the request is ambiguous, perform the audit and report proposed changes rather than editing.

## Audit Workflow

### 1. Establish scope

Locate the manuscript root, bibliography, included source files, generated figures, data tables, build instructions, venue template, and supplementary material. Check version-control status before editing. Do not assume that every nearby draft, build artifact, or reference paper belongs to the submission.

Read the full manuscript before reporting global findings. Inspect the rendered PDF when layout, figure placement, page limits, or visual quality matter.

### 2. Build a claim map

Extract the major claims from the title, abstract, introduction, contribution list, experiment headings, findings, and conclusion. For each claim, identify its evidence in the body.

Flag:

1. claims with no supporting experiment, theorem, citation, or implementation evidence;
2. claims whose scope expands between body and abstract;
3. capabilities described as demonstrated outcomes;
4. hypotheses written as causal explanations;
5. results that are correct but no longer central to the paper's framing.

### 3. Audit all reported data

Trace each headline number to its source. Recompute simple totals, percentages, rankings, and differences when source data are available.

Check the same value everywhere it appears:

1. abstract;
2. main result prose;
3. tables;
4. plots;
5. captions;
6. appendix;
7. conclusion.

When a model, task, or rerun has changed, assume every aggregate is stale until verified. Do not accept a successful compilation as evidence of data consistency.

### 4. Audit terminology, notation, and responsibility

Search for alternate names, capitalization variants, stale acronyms, undefined symbols, and one term used for multiple referents. Check that actors, policies, protocols, platforms, environments, scorers, and datasets retain distinct responsibilities.

Watch especially for prose that credits a model for deterministic work performed by the environment, or claims that the environment performs a decision assigned to the model.

### 5. Audit structure and readability

For each section and paragraph, write a short purpose label. Flag duplicate sections, late definitions, results separated from their figures, validation detail that overwhelms the scientific contribution, and conclusions collected far from the evidence they interpret.

Search for:

1. noun stacks and long enumerations;
2. one-sentence paragraphs without structural purpose;
3. abstract subsection titles;
4. repeated setup across experiment subsections;
5. related work that lists papers without a contribution boundary;
6. captions that carry analysis better placed in prose.

### 6. Audit citations and metadata

Resolve every citation key. Flag unused bibliography entries, duplicated records, missing citations for named systems or models, preprints with a canonical published version, and citations that do not support the attached claim.

Check author order, affiliations, email addresses, venue metadata, anonymous-mode settings, CCS concepts, acknowledgments, and repository links against the intended submission mode. Do not infer an affiliation, location, or license from a domain name.

### 7. Audit figures, tables, and rendering

Inspect visuals at final PDF scale. Verify label size, alignment, whitespace, clipping, overlap, arrow consistency, color meaning, panel references, and caption accuracy. Compare every plotted value with the source table.

Compile into the designated build directory. Inspect page breaks, isolated words on terminal lines, stranded headings, large blank regions, floats far from discussion, unexpected running headers, and content beyond the page limit.

### 8. Audit submission claims

Check statements about public artifacts, code, data, licenses, tags, reproducibility, maintenance, ethics, and external review against current reality. If the paper says an artifact is public, the link must work for an unauthenticated reader. Do not create extra contracts, hashes, manifests, or evidence packages unless the venue or user actually requires them.

### 9. Run focused searches

Use targeted searches after the conceptual audit. Useful categories include:

1. stale model or method names;
2. forbidden punctuation and contractions;
3. undefined figure or table references;
4. unmatched citation keys;
5. old totals and percentages;
6. internal task IDs, paths, comments, or TODO markers;
7. wording such as first, novel, guarantee, all, every, public, proven, and significant.

Searches supplement reading. They do not replace it.

## Reporting

Report findings in descending severity:

| Severity | Meaning |
| --- | --- |
| P0 | invalidates a central claim, result, artifact, or submission |
| P1 | likely reviewer objection or material inconsistency |
| P2 | local clarity, citation, visual, or formatting defect |
| P3 | optional refinement |

For each finding, give the location, observed evidence, why it matters, and the smallest safe correction. Separate confirmed defects from judgment calls.

End with:

1. what was verified;
2. what remains uncertain;
3. whether files were modified;
4. what should happen before submission.

Load [full-paper-checklist.md](references/full-paper-checklist.md) for a comprehensive audit. Load [audit-examples.md](references/audit-examples.md) when classifying a subtle inconsistency or deciding the minimum safe fix.

## Fixing Findings

When authorized to edit:

1. fix central contradictions before style;
2. update all dependent text and visuals together;
3. retain collaborator comments unless the user asks to remove them;
4. compile after each layout-sensitive batch;
5. inspect the changed pages visually;
6. rerun the focused searches;
7. report the exact changes and remaining risks.

Do not silently rewrite the paper's scientific position. Do not optimize page count by deleting evidence the user asked to retain.
