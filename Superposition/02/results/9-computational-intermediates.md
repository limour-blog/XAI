> ⬅️ 返回 [论文索引](../INDEX.MD) · §4 Features as Computational Intermediates

# From feature activations to intermediate computation

For a target versus baseline next-token logit difference $g$, the attribution of feature $i$ at token $t$ is $a_{i,t}(\nabla_{\mathbf{x}_t}g\cdot\mathbf{d}_i)$, with $a_{i,t}$ its activation and $\mathbf{d}_i$ its unit decoder direction. It approximates the difference associated with removing its current contribution. **Ablation** actually sets that activation to zero at the chosen token and reruns downstream computation. It can measure nonlinear effects and costs a separate forward pass per intervention. This is different from [generation steering](../methods/2-dataset-and-steering.md) at every position.

## Emotional inference: sad versus happy

> John says, “I want to be alone right now.” John feels

The two top-ranked features by attribution and by ablation are `1M/22623` (wanting to be alone) and `1M/781220` (sadness). The first activates from “alone” onward, while the second is active on “John feels.” The authors interpret this as evidence for both the input meaning and a downstream partial inference being present in the middle layer. Simply ranking by mean activation brings up several less informative positional or lexical features. [Figure 031](../figures/figure-031.md).

## Multi-step inference: Sacramento versus Albany

> Fact: The capital of the state where Kobe Bryant played basketball is

The top five features by ablation match the top five by attribution up to ordering: Kobe Bryant (`1M/391411`), California (`1M/81163`), “capital” (`1M/201767`), Los Angeles (`1M/980087`), and Los Angeles Lakers (`1M/447200`). The California feature is not simply a name detector; it often fires after explicit mentions of California and can contribute without that word occurring in the prompt. Eight of the ten most attributed features belong to the ten strongest ablation effects. Related prompts probe whether candidate features matter for this completion rather than merely responding to the general topic.

Only three of the ten strongest activations are among the ten largest ablation effects. The Lakers, California, and Los Angeles area-code features are ranked 70th, 97th, and 162nd by activation, respectively. In a comparison prompt asking for the Lakers’ biggest rival, Kobe Bryant and Lakers are again important to the completion “Boston,” but California and Los Angeles have low ablation effects. These are selected case studies: other baselines surface more generic trivia or geography features, and some prompts reveal few interpretable intermediate steps at the studied layer.

Figures: [032](../figures/figure-032.md), [033](../figures/figure-033.md), [034](../figures/figure-034.md). See [correlation between attribution and ablation](12-ablation-and-attribution.md). These examples identify intermediate variables that influence the output; they do not trace all computations that produce or consume those variables.
