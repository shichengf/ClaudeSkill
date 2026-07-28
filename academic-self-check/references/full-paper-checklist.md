# Full-Paper Audit Checklist

Use this checklist for the final pass. Skip items that clearly do not apply, but state what was skipped.

## Scientific story

- Does the title describe the paper's actual primary contribution?
- Do the abstract, introduction, contribution list, section order, experiments, and conclusion tell the same story?
- Is each contribution supported by a named section, figure, table, theorem, or released artifact?
- Are environment capabilities separated from benchmark results?
- Are proposed uses separated from demonstrated uses?
- Are empirical observations separated from causal explanations?
- Are limitations scoped to claims the paper actually makes?

## Abstract

- Is the problem clear before the solution appears?
- Is the introduced artifact or method named explicitly?
- Does every number appear and receive context in the body?
- Are universal words such as every, all, fully, and complete literally true?
- Does the final sentence state a supported conclusion rather than a slogan?
- Does the abstract fit the venue limit and preserve stable downstream layout?

## Introduction

- Does each paragraph follow causally from the previous one?
- Is the gap specific rather than a broad complaint about prior work?
- Is the example teaching the main contribution rather than secondary verification detail?
- Are contributions parallel in granularity and ordered like the paper?
- Are figures introduced near the concepts they explain?
- Is old framing left behind after a title or contribution change?

## Method or environment

- Are components introduced before detailed mechanics?
- Does each component have one clear responsibility?
- Can the reader follow one action from input to outcome?
- Are visibility and write authority distinguished?
- Are protocol, runtime, platform, World, policy, skill, and tool used consistently?
- Is every equation motivated and every symbol defined?
- Are rejected, read-only, or abstaining actions described without nonexistent state changes?
- Are optional extension points presented after the core system?

## Data and benchmark construction

- Is the relationship between source data, derived fixtures, and synthetic additions precise?
- Are collection, licensing, review, and redistribution claims factual?
- Does one complete task example expose the instruction, context, action interface, and scoring criteria?
- Are task families, capabilities, difficulty factors, and counts clearly distinguished?
- Are internal task identifiers absent from narrative prose?
- Is ambiguity in staged tools or hidden actions avoided?
- Is task review described accurately, including who reviewed what?

## Evaluation and results

- Is the common setup stated once?
- Are all compared models evaluated under genuinely comparable conditions?
- Are failed infrastructure runs separated from scored model behavior according to the declared policy?
- Does every figure or table have a conclusion in nearby prose?
- Are totals, means, shares, and rankings correct after the latest data update?
- Are partial-credit and zero-credit definitions clear?
- Are case-study instructions sufficient to judge the model's choice?
- Are diagnostic experiments presented with their proper denominator and scope?
- Are one-seed or one-run results described without variance claims?
- Are findings labeled as findings only when they add interpretation beyond the preceding results?

## Process records and learning claims

- Is state reconstruction explained without relying on the overloaded word replay?
- Is auditability tied to inspecting decision, validation, and consequence?
- Is verifiability tied to deterministic checks the paper actually performs?
- Are process-level reward signals described as available signals rather than trained-policy evidence?
- Is the full trace compared fairly with restricted views?
- If restricted-view errors are reported, is the reference set and collision definition clear?
- Is a result stated for this benchmark rather than generalized to all scorers?

## Related work

- Does each paragraph compare a coherent line of work?
- Does it say what prior work enables before stating what is missing?
- Is the present paper's difference specific and supported?
- Are complementary goals described as complementary?
- Does a comparison table avoid properties that are undefined or selectively favorable?
- Are recent and direct competitors covered?
- Are named protocols, benchmarks, models, and providers cited?

## Figures

- Does each figure have one primary message?
- Is the primary contribution visually dominant?
- Are text and symbols legible at final size?
- Are repeated nodes aligned and spaced consistently?
- Do arrow styles have a stable meaning?
- Is whitespace used intentionally rather than left by oversized boxes?
- Does the color scheme remain interpretable in grayscale?
- Are high-information figures restrained in color?
- Are internal titles removed when the caption already names the figure?
- Are labels in human language rather than repository jargon?
- Does the caption match the current panels and values?
- Does nearby prose explain the finding rather than restate the diagram?

## Tables

- Does the table provide exact values or a compact comparison that prose cannot provide?
- Are headers understandable without unexplained abbreviations?
- Do caption and notes define nonstandard columns?
- Are text-heavy tables better represented as a figure or prose?
- Are numeric precision and units consistent?
- Does cell shading have a stated meaning and sufficient contrast?
- Does the table fill its intended width without excessive empty columns?
- Are references better placed in nearby prose than crowded into cells?

## Layout and LaTeX

- Does the manuscript compile cleanly from the intended root?
- Are build files confined to the build directory?
- Are floats close to first substantive discussion?
- Are there large unexplained blank areas?
- Are headings stranded at a column bottom?
- Are one or two words isolated on a final line before a new paragraph?
- Are figure and table numbers correct after reordering?
- Are there unresolved references, duplicate labels, or missing citations?
- Are comments, line numbers, review markup, and internal paths absent from the submission PDF?
- Does the page count comply without unsupported template modifications?

## Submission metadata

- Are author order and affiliations confirmed?
- Are cities and countries present only when required by the template?
- Are corresponding-author and equal-contribution marks correct?
- Is the submission correctly anonymous or de-anonymized?
- Are CCS concepts relevant and nonredundant?
- Is the repository link accessible if claimed public?
- Are data and code licenses stated consistently with the repository?
- Are acknowledgments safe for the submission mode?

## Final consistency sweep

- Search each model name and verify every occurrence.
- Search each headline total and percentage.
- Search old project names and removed terminology.
- Search all figure and table labels and references.
- Compare plotted data with source data.
- Compare abstract claims with conclusion claims.
- Inspect every page of the final PDF at normal reading scale.
