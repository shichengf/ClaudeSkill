# Synthesis and Citation Workflow

## Build a synthesis matrix

Create rows for papers and columns for the taxonomy dimensions, assumptions, evidence, and limitations. Use the matrix to find repeated patterns before drafting paragraphs.

## Write pattern-first paragraphs

Weak:

> A uses a variational model. B uses a flow. C uses diffusion.

Better:

> The methods differ mainly in how they trade likelihood fidelity for architectural flexibility. Variational approaches favor flexible posteriors, flow-based methods retain exact likelihoods under stronger structural constraints, and diffusion approaches move the tradeoff to iterative sampling.

Attach citations to the clauses they support.

## Compare roles, not names

Group citations when works support the same claim. Separate them when their roles differ:

> The assumption was introduced by A, relaxed by B, and challenged empirically by C.

Do not give every paper a standalone sentence. Expand a work when it introduces the branch, supplies decisive evidence, changes a core assumption, or is necessary to understand later methods.

## Narrate a progression only when it exists

Use a developmental arc when later work explicitly addresses a known limitation:

> Early approaches established X but required Y. Later work removed Y by introducing Z, at the cost of W.

When no progression exists, compare alternatives along one design tension instead of inventing chronology.

## Handle performance numbers neutrally

Either report comparable numbers for the methods in a defined evaluation setting or keep the prose qualitative and place full results in a table. Selectively quoting impressive numbers creates promotional bias.

Check whether datasets, splits, metrics, and compute are comparable before declaring one method better.

## Canonical citations

Prefer the canonical archival publication when it exists. Use a journal extension when it materially supersedes the conference paper; otherwise cite the version readers most commonly recognize. Retain an arXiv citation when no archival version exists.

Verify title, author order, venue, year, pages, DOI, and URL from primary metadata. Do not trust a copied BibTeX entry without checking it.

## Citation placement

Place a citation immediately after the supported claim. Use the project's citation commands consistently. Do not attach one citation to a sentence containing several claims unless the source supports all of them.

Avoid paragraph tails such as:

> Additional work applies the idea to A, B, C, D, and E.

If the applications share a meaningful pattern, state it and group the citations. If they do not, omit peripheral examples or discuss them where they become relevant.

## Terminology

Choose one canonical term and record common variants once. Do not change a cited work's technical meaning to fit the survey taxonomy. When communities use the same term differently, state the distinction explicitly.
