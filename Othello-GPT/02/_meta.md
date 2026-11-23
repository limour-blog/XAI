返回 [论文索引](INDEX.MD)

# _meta — machine-readable manifest

```meta
paper_id: 02
status: done
title: Linear Representations of Sentiment in Large Language Models
lang: en
journal: arXiv
year: 2023
doi:
arxiv: 2310.15154v1
authors_short: Tigges et al.
keywords: sentiment; linear representation; directional patching; summarization motif; mechanistic interpretability
one_liner: 单一残差流方向能表征情感；在筛选后的 SST 子集上，仅消融逗号位置的该方向就使准确率下降 18 个百分点。
```

## Abstract

**Background:** The study asks how language models encode sentiment and whether the representation matters causally to behavior.

**Methods:** Five methods find sentiment directions on a templated movie-review dataset. The authors measure correlations on diverse text, run directional activation patching and ablation, and trace sentiment circuits in GPT-2 and Pythia.

**Results:** Directional patching flips 53.5% of predictions for matched phrases on a filtered Pythia-1.4B SST test subset. Circuit interventions show that sentiment can be summarized at words or punctuation without inherent valence. On a different SST subset, restricted to comma-containing prompts the Pythia-2.8B model initially gets right, removing the sentiment direction at all positions removes 76% of the above-chance accuracy; removing it at commas alone removes 36% of that same margin.

**Conclusion:** A single fitted direction captures an important part of sentiment processing across models and tasks. Intermediate summarization sites form a partial information bottleneck, rather than carrying all sentiment information.
