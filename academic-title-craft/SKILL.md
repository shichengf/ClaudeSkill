---
name: academic-title-craft
description: >
  Generate, compare, audit, and revise titles and method names for ML, AI, and
  adjacent research papers. Use when the user asks for a paper title, method
  name, acronym, renaming, title shortlist, or alignment between a title and
  the paper's actual claim. Do not use for product, company, or campaign names.
---

# Academic Title Craft

Create a title that identifies the paper's scientific contribution without
claiming more than its evidence supports. Memorability is useful only after the
title is accurate and natural.

## Establish the title contract

Inspect the manuscript or supplied summary before proposing names. Determine:

1. the paper's central question and one sentence answer.
2. the contribution type, such as a method, empirical finding, theory,
   benchmark, resource, or position.
3. the strongest claim supported by completed evidence.
4. the object being studied and the scope that limits the claim.
5. the role of any named architecture or representation in the contribution.

Do not infer that a frozen component is continually learned. Do not turn a
state estimator into a dynamics model or a query interface into planning. If
the evidence is unfinished, title the stable problem and mechanism rather than
an expected result.

## Choose one foreground

A title should foreground one of these elements:

- the scientific problem or object.
- the main supported finding.
- the mechanism that makes the result possible.
- a useful method name followed by a plain description.

Do not compress the abstract or contribution paragraph into the title. Details
that explain a secondary learning loop, loss term, benchmark, or implementation
boundary usually belong in the abstract.

## Generate title families

Draft candidates from more than one family before ranking them:

1. **Direct description:** mechanism or object followed by the task and scope.
2. **Claim statement:** the strongest supported finding in ordinary language.
3. **Method name plus description:** a distinctive name, then a clause that
   remains informative without the name.
4. **Grounded contrast:** a short contrast that expresses the actual technical
   tension demonstrated by the paper.
5. **Question:** use only when the paper is organized around resolving that
   question and a statement title would conceal the answer.

Generate acronyms after a natural title exists. Reject an expansion that uses
awkward grammar, irrelevant words, or misleading terminology merely to obtain
desired letters. The descriptive part must still work when the method name is
removed.

## Audit every candidate

Reject a title that fails any of these gates:

- **Scientific fidelity:** every capability in the title is implemented and
  evaluated or clearly presented as a formulation.
- **Scope calibration:** the title names the actual regime when a broader term
  would imply unsupported generality.
- **Natural syntax:** a reader can say the title aloud without repairing its
  grammar. Avoid ownership chains, serial enumerations, and noun stacks.
- **Role alignment:** the method name describes the component that actually
  changes or learns.
- **Searchability:** the title contains the terms that the intended research
  community would use to find the work.
- **Distinctiveness:** an exact title and method name search reveals no obvious
  collision with a closely related paper, benchmark, workshop, project, or
  package.

Treat 8 to 14 content words as an empirical prior rather than a limit. Shorter
is not better when it removes the object or scope. Longer is justified only
when each added phrase prevents a real misunderstanding.

Avoid unearned words such as `novel`, `general`, `unified`, or `foundation`.
Avoid a broad field label that does not distinguish the paper.
Do not repeat the same concept in a method name and its subtitle.

## Check collisions when a name may be public

Search the exact quoted title and method name. Also search close spelling and
acronym variants in arXiv, OpenReview, official proceedings, and code hosting
sites when available. Prefer primary records. State that the check is
preliminary because absence from search results does not establish ownership.

## Rank and present

Score candidates with scientific fidelity as the first priority. Then compare
scope precision, readability, contribution focus, searchability, and
memorability. A clever title cannot compensate for a scientific mismatch.

Present one recommendation and at most two meaningfully different alternatives
unless the user requests a longer brainstorm. For each alternative, explain
what it foregrounds and its main risk. Say directly when the existing title is
better than the new candidates.

Do not edit manuscript files until the user chooses a title or explicitly asks
for the rename. After an authorized rename, update the title, method macro,
abstract, introduction, captions, conclusion, supplementary material, and
project memory wherever the old identity remains.

## Evidence and venue patterns

Read [references/title-patterns.md](references/title-patterns.md) when the user
asks for evidence, venue comparison, acronym design, collision analysis, or a
high stakes final choice. It records the recent top conference corpus, title
families, award examples, and the limits of the observed patterns.
