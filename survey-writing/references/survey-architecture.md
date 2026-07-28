# Survey Architecture

Use this reference to plan a full survey. Adjust section names and proportions to the venue and field.

## Macro structure

### Introduction

Explain the field, why synthesis is needed now, what prior surveys cover, the present scope, the organizing framework, and the survey's contributions. A roadmap is optional and should remain short.

The gap must be specific. “Recent work is not covered” is weak. Name the missing methods, evaluation perspective, deployment regime, or cross-community connection.

### Background

Provide only the concepts and notation required to understand the taxonomy. For each concept, give its definition, intuition, and role in the survey. Cite derivations instead of reproducing textbook material.

### Taxonomy

Introduce the axes before the body sections. For each axis, explain:

1. what decision or assumption it captures;
2. why that distinction matters;
3. how category membership is decided;
4. how hybrid works are handled.

Pair the explanation with a figure or compact table.

### Main body

Give each major taxonomy branch a consistent internal structure:

1. define the branch;
2. state the problem it addresses;
3. synthesize subthemes;
4. compare representative approaches;
5. end with a branch-specific limitation or connection.

The opening and closing should not repeat the same claim. Keep introductory “shell” prose proportional to the analytical body.

### Comparative analysis

Compare across branches rather than summarize them. Useful lenses include assumptions, data access, guarantees, compute, benchmarks, robustness, and deployment constraints. Quantify corpus-level patterns when possible.

### Open problems

Connect each direction to a finding from the body or comparative analysis. Name the technical obstacle. Avoid generic requests for scale, robustness, or real-world validation without specifying what must change.

### Conclusion

Restate the organizing insight, the most important cross-cutting findings, and the highest-priority open problem. Do not introduce new papers or categories.

## Taxonomy design tests

### Conceptual test

Can each axis be explained without naming individual papers? If not, the taxonomy may be retrofitted to the corpus.

### Boundary test

Can two readers place a paper in the same category from the written definition? If not, refine the criteria.

### Resolution test

Does the taxonomy separate approaches with different assumptions or consequences while grouping cosmetic implementation variants?

### Stability test

Would a plausible new paper fit without changing the entire structure? A taxonomy should guide future reading, not only describe the current list.

## Figures and tables

Choose a tree for a genuinely hierarchical taxonomy, a matrix for two independent axes, and a layered diagram when systems differ at several stages. Avoid Venn diagrams when overlap is so extensive that membership becomes ambiguous.

A comparison table should use stable dimensions derived from the survey questions. Include a short note defining nonstandard symbols. Do not bold a preferred method unless the highlighting has a neutral, declared rule.
