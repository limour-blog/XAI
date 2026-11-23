> ⬅️ 返回 [论文索引](../INDEX.MD) · §3.1 Exploring Feature Neighborhoods

# Feature neighborhoods and splitting

The analysis compares the normalized decoder directions from the 1M, 4M and 34M runs by cosine similarity. Nearby directions often represent concepts related to the anchor through topic, context, or abstraction.

- **Golden Gate Bridge (`34M/31164353`):** Neighbors include Alcatraz and the Presidio, then places such as Lake Tahoe and Yosemite, and more distant attractions outside the region. One San Francisco feature in the 1M run corresponds to two in the 4M run and eleven finer-grained features in the 34M run. The larger dictionaries also include a cluster of earthquake features not found in the smaller neighborhood. [Figure 023](../figures/figure-023.md).
- **Immunology (`1M/533737`):** Neighborhood regions cover immunosuppression, conditions and immune responses, microscopic immune components and techniques, and more distant non-medical senses of immunity. [Figure 024](../figures/figure-024.md).
- **Inner conflict (`1M/284095`):** Nearby subregions include balancing trade-offs, legal conflict and opposing principles, and emotional struggle or guilt. The boundaries are not sharp. [Figure 025](../figures/figure-025.md).

See the authors’ [interactive UMAP](https://transformer-circuits.pub/2024/scaling-monosemanticity/umap.html). Decoder-space proximity helps search for related concepts; it does not alone identify a causal connection. Compare [coverage across sizes](7-completeness.md).
