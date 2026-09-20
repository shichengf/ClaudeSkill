# Experiment design and narration

Use this guide to organize existing results or, when asked, plan experiments. It is not a demand to reproduce the references' benchmark breadth, seeds, training scale, or audit protocols.

## Start from the question, not the available metric

Identify the central claim and the observation distinguishing it from a plausible alternative. Then choose the closest available comparison. An experiment should teach something even if the proposed method does not win.

| Question | Informative comparison | What the prose should make clear |
| --- | --- | --- |
| Does the method improve the task? | Method and relevant baseline in a stated setting | Model, evaluation population, metric, and stage |
| What contributes to the gain? | Remove or change one source or operation | What is fixed and what the variant removes |
| Where should computation go? | Change allocation across components | Total and component budgets actually compared |
| Does the diagnostic matter downstream? | Local diagnostic linked to task behavior | Intermediate and task measurements are distinct evidence |
| Does the effect extend? | Another model, task, domain, or scale | Whether the method is reused, adapted, or retrained |
| What does efficiency mean here? | Cost and quality under a specified workload | End-to-end comparison or isolated component |
| What fails and why might it fail? | Cases, subgroups, or targeted probes | Selection, observed behavior, limits of the explanation |

These are alternatives, not seven mandatory experiments. Use evidence needed for this paper's main claim. Do not prescribe more runs merely because another article reports them.

## Three evidence structures from the corpus

### Diagnose a bottleneck, then target it

Planner Matters introduces roles, varies their capacities, and uses the resulting asymmetry to motivate planner-focused training. Its later training comparison asks whether that targeting helps. The useful pattern is that a measurement makes the intervention worth trying.

Use this structure when an existing diagnostic motivates the method. Do not manufacture a chronology in which every reported experiment preceded the design. A retrospective explanatory order is fine; an invented history is not.

### Follow a proposed repair through a pipeline

CD-LAM examines a latent representation, its effect on world-model rollouts, and its effect after adaptation to executable actions. Its diagnostics and task metrics answer different questions. Readers can trace whether an upstream change reaches downstream behavior.

Use this structure when the paper has multiple stages and corresponding evidence. It does not imply every improvement is causally isolated. Specify additional training signals and unmatched workloads where they affect interpretation.

### Establish the system result, then explain behavior

StructAgent presents the main task results and new environments before examining verification and failures. RSIAgent follows aggregate performance with exploration-round behavior, stage ablations, another task setting, and observed failures. These make system behavior understandable after readers have seen the purpose and outcome.

Use this structure when the mechanism is intuitive and the main result is the natural entry point. Do not move all explanatory evidence to the appendix just because a main table looks strong.

## Choose controls that answer the actual question

For an ablation, identify the changed variable and information still available. Removing a reward differs from retaining it while changing its assignment. Scaling a component differs from adding a component. A published score under another harness is context, not a matched intervention.

For efficiency, choose the interpretation before the ratio: equal budgets, time to a specified quality, or complete practical configurations. Report whichever was measured. Do not call a wall-clock configuration comparison a verifier-only speedup. Do not equate steps when batch size or optimization reuse differs.

Preserve metric meaning. Distinguish accuracy from precision among answered questions, macro from micro averages, training reward from evaluation score, and lexical matching from semantic judgments. A metric check can increase confidence in a ranking without establishing complete factual correctness. Do not invent uncertainty estimates or describe an untested sample difference as statistically significant.

## Use existing evidence before proposing more

For a revision, map current evidence to the questions above. A useful connection may already exist in an appendix table or ablation. Improve its placement or explanation before asking for another benchmark.

If experiment planning is requested, prioritize the smallest comparison that could change the central conclusion. Explain which competing interpretation it distinguishes and what each outcome would teach. Repeated seeds, another judge, a benchmark, or a contamination audit is not automatically required by this skill. A concrete suspected error needs truthful handling; a hypothetical concern should not become an endless experiment queue.

## Describe the finding in the right order

Give the overall pattern, a representative comparison or exception, then the implication. Use subgroups to explain where the gain appears. Keep a near tie visible without repeated caveats. Treat unexpected or mixed results as findings rather than editorial problems.

A case study shows the relevant input, actual output, method response, and consequence. Keep selected cases distinct from population estimates. Failure analysis explains how an observed failure propagates rather than listing everything an agent could imagine.

## CorVer transfer example

Existing evidence supports three linked ideas: corpus counts contain a useful but incomplete signal; assigning that signal locally contributes beyond an averaged response score; evaluated training configurations combine factual-QA gains with lower complete-run time. Main benchmarks establish performance, calibration examines the signal, A1/A2/A3 separate its contribution and assignment, and popularity analysis describes where gains appear. First/Min/RelCheck provides a bounded observation about more extensive checks in one setting. Scoring checks and author-key baseline configurations clarify interpretation in the appendix. This mapping introduces no new experiment requirement.
