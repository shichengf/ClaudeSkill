# Audit Examples

These examples show how to classify a finding and choose the smallest safe correction.

## Universal lineage claim

Observed text:

> Every evaluated decision is linked to its actor, validation outcome, ordered commit evidence, and resulting state delta.

Evidence:

Rejected proposals have no commit. Read-only and abstaining decisions may have no state change.

Finding:

P1 claim-scope contradiction.

Minimum correction:

> Every evaluated decision is linked to its actor and validation outcome. Accepted state-changing decisions are additionally linked to ordered commits and resulting state changes.

## Implemented lifecycle overclaim

Observed text:

> Fulfillment, cancellation, return, refund, and dispute actions remain linked to the transaction.

Evidence:

The implementation rejects unsupported dispute requests and does not implement dispute adjudication.

Finding:

P1 implementation mismatch.

Minimum correction:

Remove dispute from the implemented lifecycle list. Do not hide the mismatch through a broader word such as after-sales if that still implies implementation.

## Changed model panel

Observed state:

A new model replaces an old model in the main table.

Audit:

Search both model names. Recompute model count, run count, total full, partial, and zero outcomes, overall rankings, family means, failure attributions, restricted-view denominators, abstract numbers, captions, appendix rows, and conclusion wording.

Finding:

Any unchanged dependent value is P0 or P1 depending on whether it affects the main result.

## Restricted-view result

Observed text:

> Final-state scoring has a 10% error rate.

Evidence:

The experiment identifies projection collisions among non-full runs in one benchmark panel.

Finding:

P1 overgeneralization.

Minimum correction:

> In this model panel, 10% of non-full runs share the accepted final-state projection for the same task and are therefore indistinguishable under that restricted view.

## Hypothesized model behavior

Observed text:

> Safety training causes stronger models to reject staged checkout.

Evidence:

Several models stop earlier, but the study does not manipulate safety training.

Finding:

P1 causal overclaim.

Minimum correction:

Report the stopping behavior as observed. Present conservative post-training as one possible explanation, not the established cause.

## Figure updated without prose

Observed state:

The figure now shows only the environment, but its caption and body still describe benchmark panels.

Finding:

P1 figure-text inconsistency.

Minimum correction:

Update the caption, first reference, accessibility description, and all panel-specific prose. Check figure numbering after recompilation.

## Long validation section

Observed state:

The paper devotes more space to internal gate counts than to benchmark construction and scientific findings.

Finding:

P2 emphasis imbalance, unless the paper's central claim is formal validation.

Minimum correction:

Keep the result needed for trust in the main paper. Move detailed check inventories to the appendix or repository. Use the recovered space for task design, main results, or analysis.

## One-word terminal line

Observed state:

One or two words occupy the final source paragraph line immediately before a new paragraph or float.

Finding:

P2 layout inefficiency.

Minimum correction:

Compress the sentence by one short phrase without deleting scientific content. Recompile and inspect the page because a small change can move a float.

## Custom template macro

Observed state:

The source overrides an internal venue macro and uses negative vertical space to fit the page limit.

Finding:

P0 or P1 formatting risk, depending on venue rules.

Minimum correction:

Restore the documented template interface. Recover space through prose or visual design. Do not assert that the override is forbidden unless the official rules say so.

## Expert review claim

Observed text:

> Independent domain experts validated every task.

Evidence:

Coauthors from industry and universities discussed task design, but no independent review record exists.

Finding:

P1 unsupported independence claim.

Minimum correction:

Describe the actual author-team and external-participant review process. Do not add independent, every, or validated without records supporting those terms.
