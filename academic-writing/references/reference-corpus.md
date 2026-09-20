# Reference corpus and synthesis

The author supplied four local PDFs in `ref/`. These notes record writing observations about those versions, not independent verification or endorsement of their scientific claims. Page numbers are PDF page numbers. Local filenames identify sources; the guides remain usable without the PDFs. Keep the PDFs out of version control.

## What each paper contributes

| Supplied source | Distinctive narrative | Useful places to inspect |
| --- | --- | --- |
| `2605.02168v1.pdf`, *Planner Matters! An Efficient and Unbalanced Multi-agent Collaboration Framework for Long-horizon Planning* | Allocation analysis motivates focused training | Abstract p. 1; problem/insight p. 2; roles pp. 3–4; scaling pp. 4–5; RL pp. 5–6; results/ablation pp. 7–9; conclusion pp. 9–10 |
| `2607.09185v1.pdf`, *Causally Debiased Latent Action Model for Embodied Action Conditioned World Models* | Concrete failures expose a representation problem; objectives and evaluation follow the diagnosis | Abstract/introduction pp. 1–2; preliminary/analysis pp. 3–4; objectives pp. 4–5; setup/staged evaluation pp. 5–8; efficiency/ablation pp. 8–9; related work/conclusion pp. 9–10 |
| `2607.11388v1.pdf`, *StructAgent: Harness Long-horizon Digital Agents with Unified Causal Structure* | A growing-history problem organized around state and workflow | Abstract p. 1; introduction pp. 1–3; method pp. 4–5; main/extension results pp. 6–8; diagnostics/failures pp. 8–10; related work/conclusion pp. 10–12 |
| `ExRSI.pdf`, *RSIAgent: Autonomous Exploration for Recursive Self-improvement in New Environments* | Unfamiliar environments motivate exploration and reusable memory | Abstract p. 1; introduction pp. 2–3; roles/stages pp. 4–6; results/rounds/ablation pp. 8–9; failures pp. 9–11; related work/conclusion pp. 12–13 |

## Positioning is part of the lesson

The papers connect their concrete systems to large research topics: long-horizon planning, controllable world models, structured agents, and recursive self-improvement. Their titles and introductions make the intended significance visible. Learn this ambition alongside their explanatory clarity. Removing a supported hook in the name of caution loses an important part of the reference style.

For CorVer, the connection is process supervision beyond math and code and the cost of repeated neural verification. Preserve this positioning while explaining exactly what corpus feedback replaces. Confidence should follow the demonstrated contribution; it need not await proof of a universal claim.

## Shared habits

**An identifiable problem before a component inventory.** Each introduction makes a difficulty concrete before presenting named pieces. Readers understand why the method might help before learning the full implementation.

**A few organizing distinctions.** Planner versus actor versus memory; action-related versus context-related variation; state versus workflow; broad versus deep exploration. Returning to these distinctions gives each detail a place. Another paper needs its own distinctions, not these nouns.

**Stable objects connect sentences.** Plans move to actors, evidence updates state, memories enter the next attempt, and latent actions enter a world model. A sentence operates on something the previous sentence made familiar.

**Design and evaluation use the same language.** Capacity allocation is tested by changing component capacity. State-based mechanisms are examined through verification and recovery. Conditioning representations are examined through action following. Exploration stages are compared as stages. This correspondence explains why each experiment is present.

**Results are decomposed into observations.** The papers distinguish aggregate gains, subgroup behavior, another environment, and remaining failures. Representative values support observations rather than substitute for them.

**Concrete failures support a next question.** The agent papers trace decisions and evidence through a failure. CD-LAM distinguishes plausible appearance from action following. A limitation is understandable when its consequence is visible.

## Differences that prevent a rigid template

Planner Matters places motivating empirical analysis before its final RL method. StructAgent leads with a system abstraction and analyzes behavior after results. CD-LAM uses a diagnostic section and evaluates successive stages. RSIAgent uses roles, stages, and examples to explain an iterative process. No single section order is common to all four.

Titles include a finding-led slogan, named frameworks, and a direct technical description. Abstracts differ in space devoted to diagnosis and components. Some sections use questions, others declarative headings. Contribution counts, lists, equations, and placement of related work vary. Choose according to the current idea and venue.

The papers also contain dense passages, repeated qualifiers, strong causal language, long inventories, and occasional grammatical awkwardness. Do not reproduce these merely because the author likes the papers overall. The current preference is fluent discovery-led prose with limited defensive language. A reference's confident interpretation is not evidence for the current manuscript.

## Applying the synthesis to CorVer

The transferable structure is signal, assignment, and observed learning behavior. The closest prior methods provide the starting point: counts used at inference and sentence-level learning with neural verification. CorVer explores using the counts during training and assigning feedback locally.

A coherent route is: factual QA needs affordable local feedback; entity co-occurrence provides an incomplete signal; the method maps counts to sentence and token feedback; task results establish utility; calibration and ablations clarify the signal and assignment; efficiency and subgroup results describe practical behavior; the appendix holds configurations, scoring checks, and bounded diagnostics.

Keep First/Min/RelCheck within its tested setting. Keep single-run and metric scope where relevant. Do not turn the article into a theoretical guarantee that weak verification is always sufficient or import agent-specific causal claims. These are prose and organization exemplars, not factual-QA baselines or citations required in CorVer.
