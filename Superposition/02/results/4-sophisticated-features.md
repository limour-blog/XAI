> ⬅️ 返回 [论文索引](../INDEX.MD) · §2.2 Sophisticated Features

# Context-sensitive code features

## Code errors (`1M/1013764`)

The feature activates on a misspelled variable in a Python addition function, on analogous programming errors in C and Scheme, and on natural examples of bug reports and exceptions. It does not respond to the tested English typos in the same way. These controls favor an interpretation related to programming errors rather than the particular identifier, a single programming language, or misspellings in general.

Causal comparisons include clean code receiving a positive clamp and buggy code receiving a negative clamp. Increasing the feature on clean code causes the model to predict a nonexistent error; reducing it on buggy code can make the model predict the result of the corrected code. The reported rewriting is sensitive to the prompt. The interventions and the activation examples test different parts of the interpretation.

Figures: [010](../figures/figure-010.md), [011](../figures/figure-011.md), [012](../figures/figure-012.md), [013](../figures/figure-013.md), [014](../figures/figure-014.md), [015](../figures/figure-015.md), [016](../figures/figure-016.md), [017](../figures/figure-017.md).

## Functions that implement addition (`1M/697189`)

An addition feature fires at the end of a definition implementing addition and at later references to the function. The same identifier `bar` activates the feature if its function adds numbers but not if it multiplies. This is evidence that it follows what the function does, not simply what the function is called. It is among the ten strongest attributions on a prompt requiring prediction of the output of code that invokes an addition function.

Figures: [018](../figures/figure-018.md), [019](../figures/figure-019.md), [020](../figures/figure-020.md). For the distinction between attribution and ablation, see [computational intermediates](9-computational-intermediates.md).
