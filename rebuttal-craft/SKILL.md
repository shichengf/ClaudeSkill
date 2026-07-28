---
name: rebuttal-craft
description: >
  Skill for crafting and revising rebuttals to peer-review feedback in ML/AI
  research contexts. Trigger this skill whenever the user asks to write, revise,
  or audit a rebuttal, author response, reviewer reply, meta-review response, or
  any formal response to peer-review comments. Covers strategy by reviewer type,
  cross-rebuttal consistency, character budget discipline, and common credibility
  pitfalls. Use alongside the academic-writing skill, which provides baseline
  formatting, notation discipline, and prose conventions; rebuttal-craft layers
  rebuttal-specific strategy on top of those rules.
---

# Rebuttal Craft Skill

This skill governs the production of rebuttals and author responses to peer
review. Rebuttals are technical instruments, not defensive essays. Every
sentence must either (a) resolve a specific reviewer concern, (b) provide new
evidence, or (c) commit to a concrete revision. Padding kills rebuttals.

This skill assumes the baseline academic-writing skill is active for prose
formatting, notation discipline, and self-consistency. Layer this skill on top
when working on rebuttals.

After the response is drafted, use the academic-self-check skill to verify
cross-reviewer consistency, numerical agreement with the manuscript, citation
support, and promised revisions.

---

## 1. Strategic Principles

A rebuttal is not a defense; it is a technical clarification. The goal is to
resolve misunderstandings and provide new evidence, not to argue that the
reviewer is wrong.

(a) **Prioritize factual corrections**: If a reviewer misunderstands the method,
correct the misunderstanding with a precise quote from the paper plus
clarification. Do not paraphrase the reviewer's concern in a way that softens
it; address it directly.

(b) **New experiments must be airtight**: Any new result introduced in a
rebuttal will receive extra scrutiny. Verify that new numbers are internally
consistent and do not contradict the main paper. If a new experiment shows
surprisingly strong results, work out the mathematics of why before including
it.

(c) **Character budget discipline**: Most venues impose strict character limits
(e.g., 5000 characters for ICML 2026). Every sentence must earn its place. Cut
all padding, acknowledgments, and redundant restatements of the reviewer's
concern. When trimming, prioritize cutting (in order): sycophantic openings,
generic future direction speculation, surface-level application examples, and
verbose closing sentences.

(d) **Cross-rebuttal consistency**: All rebuttals for the same paper must use
identical numbers, terminology, and framing. If one rebuttal says the baseline
scores 0.921 and another says 0.925, the reviewers will notice.

---

## 2. Make the Reviewer's Life Easy

Reviewers handle dozens of papers. The easier you make it for them to verify
your claims, the more likely they are to engage positively. Concrete rules:

(a) **Inline everything**: Never say "see Appendix D.3 for details." Summarize
the key idea from the appendix in one or two sentences so the reviewer does not
need to leave the rebuttal. If the proxy is the ratio of vertical to total
velocity, say so directly rather than pointing elsewhere.

(b) **Describe experimental procedures specifically**: Do not say "we test
label noise." Say "we randomly flip 20% of training samples' domain labels to
a uniformly chosen incorrect domain." The reviewer should be able to picture
the experiment from the rebuttal alone.

(c) **Merge related concerns under one heading**: If a reviewer lists Weakness
1 and Key Question (a) that address the same underlying issue, respond once
under a combined heading rather than artificially separating them. This avoids
repetition and shows you understand the reviewer's actual concern.

(d) **Revision promises must say HOW**: "Line 090 revised" is useless. "Line
090 revised to state that TRACE proves recoverability under the convex
combination assumption, rather than claiming the assumption is physically
inherent" is actionable.

---

## 3. Rebuttal Strategy by Reviewer Type

Reviewers differ in their stance and expectations. Tailor the rebuttal
accordingly:

(a) **Critical reviewer (low score, specific technical objections)**: Focus
entirely on addressing the objections with evidence. Every sentence should
resolve a specific concern. Avoid padding. If the reviewer says "I will raise
my score if X," then X must be the central focus of the rebuttal.

(b) **Skeptical reviewer (low score, broad concerns about applicability)**:
Provide new experiments that directly test the concern. Theoretical arguments
alone will not persuade; empirical evidence is necessary. Show that the method
works under weakened assumptions.

(c) **Supportive reviewer (high score, no specific objections)**: This reviewer
is a potential champion for the paper. Frame new experiments as strengths of
the method, not just as responses to other reviewers. Give them concrete
ammunition: "TRACE demonstrates robustness to 50% domain impurity (Weight Corr
>0.96), simplex-constrained recovery outperforms unconstrained by +0.015 in
correlation, and sample efficiency degrades gracefully (Corr >0.96 at 10%
training data)." Each result should read as a reason this paper deserves
acceptance.

(d) **Silent reviewer (medium score, minimal feedback)**: Proactively address
the most likely unstated concerns (often overlap with other reviewers' points).
Be concise; this reviewer may not engage deeply during discussion.

---

## 4. Cross-Rebuttal Audit Protocol

Before submitting rebuttals, perform a systematic cross-rebuttal audit:

(a) **Numerical consistency**: Extract every number from all rebuttals and
verify that identical experiments yield identical numbers everywhere.

(b) **Isolated data points**: If an experimental result appears in only one
rebuttal (but not in the others that discuss related topics), this creates
suspicion when reviewers cross-read. Either include the result in all relevant
rebuttals, or remove it.

(c) **Terminology alignment**: The same metric must have the same name
everywhere. If one rebuttal calls it "Weight Corr" and another calls it
"α-Corr," reviewers will notice.

(d) **Framing alignment**: If one rebuttal presents a result as a limitation
while another presents the same result as a strength, the contradiction
undermines both.

---

## 5. Structure of a Single Rebuttal

For each reviewer concern, use this structure:

(1) One-sentence summary of the concern (paraphrased, not quoted).
(2) Direct response with evidence: a clarification, a citation to the paper,
or new experimental data.
(3) Explicit takeaway: what the reviewer should conclude from the evidence.
(4) If applicable, a concrete revision plan: "We will add this clarification
to Section X in the revision."

Group related concerns under a single heading when they share an underlying
issue. Use ordered labels (Q1, Q2, Q3 or W1, W2, W3) that match the reviewer's
numbering when possible.

---

## 6. Common Pitfalls

(a) **Claiming robustness that is architecturally trivial**: If the model's
encoder does not use domain labels as input, then robustness to domain label
noise is a trivial consequence of the architecture, not a meaningful empirical
finding. Presenting it as the latter damages credibility. Report the result,
but do not claim causal attribution (e.g., do not say "the transition prior
provides a meaningful identifiability signal" when the true reason is that the
encoder ignores labels).

(b) **Surprisingly strong results without explanation**: If a degradation
experiment (e.g., 50% contamination) produces unexpectedly good results,
explain WHY mathematically before the reviewer asks. For example, if
contamination at ε=50% with K=5 domains still preserves each domain's specific
signal because the critical threshold is ε=(K−1)/K=80%, state this explicitly.
An unexplained strong result invites scrutiny of the experimental design
itself.

(c) **Non-monotonic results**: If a degradation experiment (e.g., increasing
contamination from 0% to 50%) produces non-monotonic metrics, this is a red
flag. Either the experiment has a bug, or there is a mathematical explanation
(e.g., symmetric label noise preserving partial signal). Either way, the
non-monotonicity must be explained, not hidden.

(d) **Overly strong claims**: "Our method is the first to..." should be
verified exhaustively. "To the best of our knowledge, our method is the first
to..." is safer but still requires a thorough literature search.

(e) **Undermining your own theory**: If the theoretical contribution requires
assumption A, the experiments must not inadvertently argue that assumption A
is unimportant. Every empirical framing choice should be checked for
consistency with the theoretical claims.

(f) **Answering the question that was asked, not an adjacent one**: Read the
reviewer's question literally. If they ask "how to handle K≫d without
increasing d," a table showing improvement as d increases does not answer the
question. Provide evidence at fixed d.

(g) **Listing a small fixed number of applications**: Enumerating exactly N use
cases (e.g., "three domains: manufacturing, clinical, autonomous") can backfire
by implying the method is limited to those N domains. Either provide a
principled characterization of the class of applicable problems, or give a
broader framing: "domains where pure-regime data is abundant but transitions
are scarce, such as manufacturing, clinical settings, and autonomous systems."

(h) **Overconfident real-world claims**: Stating "10-20% impurity is realistic
in practice" without citation or evidence is a credibility risk. The reviewer
may ask "How do you know?" If you cannot back a real-world applicability claim
with a reference or data, soften it or remove it.

---

## 7. Rebuttal Tone

Be direct, factual, and respectful. Avoid:

(a) Sycophantic openings ("We sincerely thank the reviewer for their valuable
time and constructive feedback"). Reviewers see through this and it wastes
characters.

(b) Defensive language ("We respectfully disagree with the reviewer's
characterization"). Instead, state the fact: "The paper uses lag-L, not lag-1
(see Equation 5, Section 3.2)."

(c) Vague promises ("We will improve the writing in the revision"). Be
specific: "We will add a paragraph in Section 4.1 clarifying the distinction
between training-time and inference-time K-selection."

(d) Lobbying for score changes ("We would be grateful for reconsideration of
the score"). Let the evidence speak. If the reviewer said they would raise
their score, do not quote this back at them.

---

## 8. Pre-Submission Rebuttal Checklist

Before posting each rebuttal, verify:

(1) Character count is within the venue limit (count raw characters including
any markdown formatting the venue specifies).

(2) Every number in the rebuttal matches the same number in the main paper
and in all other rebuttals for this submission.

(3) No experimental result is isolated to a single rebuttal — if it bears on
multiple reviewers' concerns, it appears in all relevant rebuttals.

(4) Every revision promise specifies what will change and where ("Section X.Y
will be updated to ..."), not just "we will revise".

(5) No reference to the appendix or supplementary material without also
inlining the key idea in the rebuttal itself.

(6) Rebuttal framing does not inadvertently undermine the paper's theoretical
contributions or limitations statement.

(7) Sycophantic openings, generic future-direction speculation, and lobbying
phrases are removed.

(8) For each reviewer concern, the response structure (concern → evidence →
takeaway → revision plan) is complete.

(9) Surprisingly strong results carry their mathematical explanation in the
same rebuttal that introduces them.

(10) Terminology and metric names are aligned across all rebuttals for the
submission.
