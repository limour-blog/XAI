> ⬅️ 返回 [论文索引](../INDEX.MD) · §2.1 Four Examples of Interpretable Features

# Four examples: specificity and sensitivity

The authors select four feature directions with relatively straightforward interpretations. They score about **1,000** nonzero activations per feature with Claude 3 Opus; some examples are also checked manually. The rubric is 0 for irrelevant, 1 for vaguely related or away from the highlighted text, 2 for loosely related or nearby, and 3 for a clean match. The strongest activations closely match the proposed meanings, whereas weaker ones more often correspond to related ideas or ambiguous tokens.

| Feature | Interpretation and examples |
| --- | --- |
| `34M/31164353` | Golden Gate Bridge. Strong activation on direct references; weaker activation on other landmarks and similar bridges. |
| `34M/9493533` | Brain sciences. Neuroscience, cognition, psychology, and related academic material. |
| `1M/887839` | Monuments and popular tourist attractions, including the Eiffel Tower and the Sistine Chapel. |
| `1M/3` | Transit infrastructure. Includes trains, ferries, bridges, and tunnels; some weaker examples are only loosely related. |

**Specificity** asks whether the proposed concept is present given an activation. **Sensitivity** asks whether a feature activates given the presence of the concept. The dataset-backed ratings address the former; translation of the Golden Gate Bridge Wikipedia lead into several languages gives a qualitative check of the latter, not a general estimate. In those translated examples, the Golden Gate Bridge feature is the top feature by mean activation. Relevant photos also activate several of the features, despite text-only training. This section deliberately selects interpretable features; see [random feature comparison](5-features-vs-neurons.md) for a broader sample.

Figures: [005](../figures/figure-005.md), [006](../figures/figure-006.md), [007](../figures/figure-007.md), [008](../figures/figure-008.md). See also [effects of clamping](3-behavior.md).
