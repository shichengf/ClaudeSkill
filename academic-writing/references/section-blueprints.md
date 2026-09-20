# Section blueprints

Use the section's job to decide what to write. The four reference papers share explanatory habits, but their structures differ. Adapt these patterns to the contribution and available evidence. They are not fixed paragraph counts.

## Title: choose the idea readers should remember

The corpus shows three useful choices:

- **Finding first:** *Planner Matters!* names an experimentally supported asymmetry; its subtitle identifies the system and setting. Use this when the finding is central, not when a minor ablation happens to be striking.
- **Method plus mechanism and task:** the StructAgent and RSIAgent titles make the organizing mechanism visible after the name.
- **Direct technical description:** the CD-LAM title identifies what is changed and where it matters without a slogan.

A useful title names the object of study and the distinctive contribution. Choose one principal emphasis rather than stacking novelty, efficiency, robustness, generality, and safety claims. Every technical word must earn its place in the paper. Do not borrow "causal," "unified," or "recursive" merely because the exemplars use them. A broad contrast such as "Beyond Math and Code" can be an effective title when it locates the real contribution in a larger research agenda. Preserve the author's preferred hook; do not automatically replace it with a narrower method-name title. A method name may be prominent in the abstract rather than the title.

## Abstract: tell a small complete story

Open with a consequential research problem and make its obstacle concrete. A strong field-level connection can establish why the reader should care before the mechanism appears. Introduce the paper's answer early enough that background does not dominate. Explain the essential mechanism in language the reader can understand before seeing the formalism. Select evidence supporting the central promise, then state what has been learned.

A diagnosis-led paper can move from an observed failure to a repair and its measured consequences, as CD-LAM does. A system paper can move from a practical difficulty to complementary components and their evaluation, as StructAgent and RSIAgent do. A finding-led paper can introduce the analysis before the final training method, as Planner Matters does.

Use numbers selectively: define the comparison's scope and report the results supporting the title. Do not compress every secondary benchmark into the abstract. Avoid opening with several sentences of field history or closing with an unsupported promise of broad impact. Give the central contribution its strongest supported expression. Put a qualifier next to a claim only when it changes how that claim should be understood; the abstract need not repeat every limitation discussed later.

## Introduction: let the idea follow from the problem

Connect the work to the larger research agenda, then move to a difficulty the reader can picture. A sharp bottleneck or a memorable contrast should survive stylistic revision when the paper gives it concrete substance. Explain what current approaches achieve and where the relevant difficulty remains. Name the missing capability, distinction, or experimental question. Then introduce the insight and describe how the proposed method acts on it.

A useful transition carries an unresolved issue forward. In Planner Matters, separating roles leads to the question of where capacity should go. In StructAgent, ambiguous progress leads to shared state and controlled updates. In CD-LAM, visually plausible but poorly controlled rollouts lead to examining the conditioning representation. In RSIAgent, unfamiliar environments lead to exploration and reusable memory.

Use a concrete example when it makes the difficulty easier to see. It should illustrate the mechanism rather than add an unrelated application story. A human-learning analogy is optional. Cite the closest preceding method where it explains the starting point, and state the new use or change directly.

Preview findings after the mechanism is understandable. Contributions should reflect what the paper adds: a diagnostic finding, method, benchmark, or supported empirical result. Do not count a routine implementation component as a separate scientific contribution. Use a contribution list only if it improves scanning under the venue's format.

## Preliminaries and problem statement: define the task boundary

Explain what the model receives, what it produces, what changes over an interaction or training step, and how success is measured. Define only notation used later. Distinguish training supervision from test-time input at the point of use.

A separate preliminary section is useful when the formal task is unfamiliar or reused throughout the paper. Otherwise fold it into the method. Do not add generic algorithm tutorials to make the paper look more formal.

## Method: purpose, operation, consequence

Give an overview the reader can hold in mind, then follow the actual path of information. Introduce each component by its role. Explain its input and operation, define the relevant equation or rule, and show how its output reaches the next component.

Relate multiple objectives to the difficulties they address, as CD-LAM does. Explain interfaces and responsibilities of cooperating components, as the agent papers do. Do not justify every implementation choice separately. Ordinary settings belong in setup or the appendix unless they define the method.

Keep the algorithm faithful. "First valid pair" differs from "all pairs"; local feedback differs from a response average. Simpler prose must not erase such distinctions. A concise worked example can replace a dense paragraph when it exposes the operation more clearly.

## Experimental setup: make the comparison interpretable

State the common task, models, datasets, baselines, metrics, and principal budget once. Put shared conditions together. Identify the main comparison and distinguish additional training, transfer, calibration, and qualitative inspection.

Readers should know what the model sees, which checkpoint is scored, and what the metric means. Exact optimizer settings, prompts, full configurations, and implementation edge cases usually belong in the appendix. Do not present a project-specific baseline as a full reproduction of a published recipe when only key settings were transferred.

## Results: organize by what the reader learns

Begin a subsection with its scientific purpose or principal observation. Explain the comparison briefly if new. Give the few values needed to see the pattern. Then interpret the result within its scope.

Useful distinctions include where gains are largest, which component responds to an intervention, how the pattern changes with scale, whether accuracy and cost improve together, and where a gain does not extend. Do not narrate every row. A small disadvantage can be stated naturally alongside the overall pattern.

For an ablation, explain what information or operation the variant removes. Group results by the mechanism being examined. If an intervention improves one metric but worsens another, explain which question each metric answers. Do not force all evidence into a unanimous success story.

Use [experiment-design.md](experiment-design.md) to organize evidence or plan a missing comparison when experiment planning is requested.

## Analysis and discussion: explain behavior

Answer a question left open by aggregate results. A case, diagnostic, subgroup comparison, or curve should illuminate an actual behavior. Show how an error occurs and what it affects. Separate the observation from a plausible mechanism, especially when no intervention isolates it.

An interesting result can be that a simpler check learns better, a larger model does not repair a bottleneck, or an effect concentrates in a subgroup. Preserve those distinctions instead of flattening them into "our method is effective." Do not turn discussion into an anticipated rebuttal.

## Related work: locate the contribution

Group prior work by the relevant problem, information source, or mechanism. Explain what a group enables, then where the present method fits. Name the closest predecessor and what is reused or changed. Complementary methods need not be described as deficient.

Use a comparison table when several works share multiple important comparison dimensions. Avoid inventing gaps or claiming exhaustive coverage from a few citations. Keep citation provenance intact during stylistic revisions.

## Limitations and conclusion: close the argument

State limitations materially affecting interpretation: a signal cannot inspect certain claims, a study covers a particular setting, or an observed failure remains unresolved. Connect a limitation to its consequence and, where supported, an informative example. Detailed diagnostics can live in the appendix.

The conclusion reconnects the motivating difficulty to the finding and mechanism. Synthesize what the comparisons taught rather than copy the abstract or list every score again. A next direction should follow from an observed boundary, without claiming it is already solved. Do not enlarge a narrow result into a universal design law.

## Appendix: precise and navigable

Organize by scientific purpose: setup and data, algorithm and implementation, complete results, then targeted diagnostics and cases. Short openings explain why a table or protocol is present. Keep symbols and metric names identical to the main text. Captions distinguish conditions needed to read their tables without repeating a page of setup.

Retain baseline explanations and metric checks when they clarify interpretation. Avoid development logs, repeated disclaimers, and hypothetical failure catalogues. Preserve actual model responses as artifacts; do not polish their wording. Do not invent unavailable reproduction details or promise an unauthorized release.

Acknowledgments, author contributions, AI-use statements, ethics statements, and data/code availability follow the venue and actual facts. They are not places to imitate another paper's claims or invent participation, approvals, or release status.
