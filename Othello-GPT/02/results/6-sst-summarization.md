返回 [论文索引](../INDEX.MD) · 结果

# 4.3. Validating summarization behavior in SST

Append `Review Sentiment:` to SST inputs and compare `positive` with `negative`, requiring the winning label to be in the top ten predicted tokens. Keep examples Pythia-2.8B classifies correctly with at least one comma, giving a 100% baseline on the retained subset. Commas were not selected for specifically ending sentiment phrases.

| Intervention | Logit-difference drop | Accuracy drop | Accuracy after ablation |
|---|---:|---:|---:|
| DAS sentiment direction at all tokens and layers | 71% | 38 points | 62% |
| Random directions at all tokens (control) | <1% change | <1% change | — |
| DAS sentiment direction at all comma positions | 18% | 18 points | 82% |
| Replace entire comma activation with layerwise mean | 17% | 19 points | 81% |

The 38-point drop accounts for 76% of the 50-point margin above chance. Comma-only directional ablation removes 18 points, or 36% of that above-chance margin, and nearly half of the full directional-ablation effect. The result concerns the filtered subset, not the overall accuracy on SST.

See [causal methods](../methods/3-causal-interventions.md) and [related toy results](5-punctuation-summarization.md).
