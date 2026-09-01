# Evidence and Patterns for ML Paper Titles

This reference summarizes a title corpus collected on 2026-09-01 from official
2025 proceedings. It supports title decisions but does not turn frequency into
a quality rule.

## Corpus

The corpus contains 17,453 accepted paper titles. Duplicate title entries were
removed within each source. Word counts treat an alphanumeric sequence with an
internal hyphen as one token.

| Venue | Titles | Median words | 90th percentile | Colon | Question |
| --- | ---: | ---: | ---: | ---: | ---: |
| NeurIPS 2025 | 5,823 | 9 | 13 | 54.4% | 2.3% |
| ICML 2025 | 3,330 | 9 | 13 | 46.7% | 3.0% |
| CVPR 2025 | 2,871 | 9 | 13 | 66.8% | 1.1% |
| ICLR 2025 | 3,827 | 9 | 12 | 50.5% | 3.3% |
| ACL 2025 long papers | 1,602 | 10 | 14 | 65.0% | 5.1% |

Official sources:

- [NeurIPS 2025 main conference proceedings](https://proceedings.neurips.cc/paper_files/paper/2025/vol38-main-conference)
- [ICML 2025 proceedings](https://proceedings.mlr.press/v267/)
- [CVPR 2025 open access proceedings](https://openaccess.thecvf.com/CVPR2025?day=all)
- [ICLR 2025 paper list](https://iclr.cc/virtual/2025/papers.html)
- [ACL 2025 long papers](https://aclanthology.org/2025.acl-long.0/)

The venue pages differ in track coverage and metadata conventions. These counts
describe recent title practice. They do not estimate acceptance probability or
show that a title structure caused scientific impact.

## Stable observations

The median title has nine or ten words. Most titles above the 90th percentile
have more than twelve to fourteen words, depending on venue. This supports a
short default, but it does not justify deleting a necessary scope term.

Colon titles are common. A colon often separates a short method or dataset name
from a descriptive clause. In the corpus, 39.6% to 64.0% of all titles place no
more than four tokens before the colon. This structural count includes phrases
that are not method names, so it is an upper bound on branded titles.

Questions are rare. Even ACL, which has the highest question rate in this
corpus, uses them in only 5.1% of long paper titles. Openings such as
`Towards`, `Beyond`, `Rethinking`, `Why`, and `How` together account for only
4.1% to 7.9% of titles across the five venues.

## What award titles show

Award titles demonstrate several successful families rather than one formula.
They are examples of well matched titles, not evidence that wording produced an
award.

### Direct claim

ICLR 2025 recognized *Safety Alignment Should be Made More Than Just a Few
Tokens Deep* and *Learning Dynamics of LLM Finetuning*. ACL 2025 recognized
*Language Models Resist Alignment: Evidence From Data Compression*. These
titles foreground a conclusion or phenomenon and therefore carry a high burden
of evidence.

Sources: [ICLR 2025 awards](https://blog.iclr.cc/2025/04/22/announcing-the-outstanding-paper-awards-at-iclr-2025/),
[ACL 2025 awards](https://2025.aclweb.org/program/awards/).

### Name plus precise description

ICLR 2025 recognized *AlphaEdit: Null-Space Constrained Model Editing for
Language Models*. CVPR 2025 recognized *VGGT: Visual Geometry Grounded
Transformer* and *MegaSaM: Accurate, Fast and Robust Structure and Motion
from Casual Dynamic Videos*. The name works because the clause after the colon
identifies the technical object and task without relying on the acronym.

Sources: [ICLR 2025 awards](https://blog.iclr.cc/2025/04/22/announcing-the-outstanding-paper-awards-at-iclr-2025/),
[CVPR 2025 awards](https://cvpr.thecvf.com/Conferences/2025/BestPapersDemos).

### Descriptive mechanism

NeurIPS 2025 recognized *Gated Attention for Large Language Models:
Non-linearity, Sparsity, and Attention-Sink-Free*. CVPR 2025 recognized
*Neural Inverse Rendering from Propagating Light*. These titles state the
mechanism and target directly. They do not need a method brand.

Sources: [NeurIPS 2025 awards](https://blog.neurips.cc/2025/11/26/announcing-the-neurips-2025-best-paper-awards/),
[CVPR 2025 awards](https://cvpr.thecvf.com/Conferences/2025/BestPapersDemos).

### Grounded contrast or metaphor

ICML 2025 recognized *Train for the Worst, Plan for the Best: Understanding
Token Ordering in Masked Diffusions* and *Roll the dice & look before you
leap: Going beyond the creative limits of next-token prediction*. Their first
clauses are memorable because the paper studies the stated contrast. A phrase
with no technical counterpart in the experiments would only add noise.

Source: [ICML 2025 awards](https://icml.cc/virtual/2025/awards_detail).

## Archetype selection

| Paper identity | Strong default | Main risk |
| --- | --- | --- |
| New method with a useful name | `Name: mechanism for task` | The name displaces the scientific object |
| Empirical discovery | Direct statement of the finding | The claim exceeds the tested scope |
| Theory | Object, guarantee, or limitation under its assumptions | The title hides the setting that makes the result true |
| Benchmark or dataset | `Name: what is measured in which regime` | The subtitle becomes a feature list |
| System | System capability plus its operating boundary | Interfaces are presented as demonstrated outcomes |
| Position paper | Explicit position or thesis statement | A broad slogan replaces the argument |
| Early framework with pending results | Stable problem and proposed mechanism | Expected results appear as established findings |

## Common failure modes

### Acronym first

Desired letters are chosen before the scientific phrase. The expansion then
adds weak words or broken grammar. Reverse the process. Write a natural title,
then test whether a short name emerges.

### Contribution list as subtitle

The title names a state, its policy, its objective, its budget, and its query
interface. This usually creates a serial enumeration and prevents any one idea
from becoming the paper's identity.

### Misnamed learning target

A component appears in the method name even though that component is frozen or
incidental. Name what changes, what is predicted, or what the paper establishes.

### Field label without a contribution

A title uses only a broad area name. It is difficult to search and can imply
ownership of a research direction larger than the paper's evidence.

### Repetition across the colon

The method name and subtitle express the same concept twice. Remove the name or
replace the subtitle with the missing scientific object.

### Unsupported declarative title

A concise statement can erase the population, environment, or evaluation
boundary that makes it true. Nature Human Behaviour explicitly warns that
declarative titles can overstate confidence when nuance is removed.

Source: [Writing more informative titles and abstracts](https://www.nature.com/articles/s41562-023-01596-8).

## Practical title audit

Ask these questions in order:

1. What exact claim will a reviewer infer from the title alone?
2. Which completed result or formal statement supports that inference?
3. Which word would imply a capability the paper does not test?
4. What is the one concept a reader should remember after scanning the title?
5. Can the title be spoken naturally without unpacking an acronym?
6. Does the descriptive clause work after removing the method name?
7. Do the important search terms appear in ordinary language?
8. Does an exact search reveal a closely related use?

IEEE recommends titles that are specific, concise, and descriptive. It also
advises against filler such as `new` and `novel`. Nature's editorial advice
adds two important constraints. A title should use searchable field terms, and
every declarative claim must be supported by the data.

Sources: [IEEE conference paper structure](https://conferences.ieeeauthorcenter.ieee.org/write-your-paper/structure-your-paper/),
[Nature Index title guidance](https://www.nature.com/nature-index/news/how-to-write-a-good-research-science-academic-paper-title),
[Why the title of your paper matters](https://www.nature.com/articles/s41562-021-01152-2).
