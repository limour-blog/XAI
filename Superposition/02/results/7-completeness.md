> ⬅️ 返回 [论文索引](../INDEX.MD) · §3.2 Feature Completeness

# Coverage improves with width but remains incomplete

For each target concept the authors enter a short prompt (such as “The physicist Richard Feynman”), take the top five activations at the last token, have Sonnet explain the corresponding features and have a human judge whether one of the explanations identifies the target specifically. This procedure tests whether the search can identify a dedicated feature, not whether the whole representation contains the information.

- Sonnet can list the London boroughs, but the search recovers corresponding features for only about **60%** of them in the 34M SAE.
- For elements, cities, animals, and fruits and vegetables (100–200 relatively unambiguous names per category), common concepts are found more often. Wider SAEs tend to recover features for rarer concepts. Frequencies are estimated in a data proxy by counting names, with false positives when a name has other meanings (for example, *lead*).
- The frequency at which detection exceeds 50% is slightly lower than the inverse of the number of alive features; the 34M SAE has about 12M alive features. Rescaling frequency by the alive count roughly overlays the curves. The relationship motivates a scale estimate, not a guarantee that rare concepts have one dedicated unit or that the rule extrapolates indefinitely.

The authors cannot isolate the influence of frequency in the SAE dataset from frequency in Sonnet’s pretraining mixture. Missing a dedicated direction can also reflect a composition of related features or a limitation of the search.

Figures: [026 — elements](../figures/figure-026.md), [027 — four categories](../figures/figure-027.md), [028 — rescaled curves](../figures/figure-028.md).
