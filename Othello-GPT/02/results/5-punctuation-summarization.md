返回 [论文索引](../INDEX.MD) · 结果

# 4.2. Exploring and validating summarization behavior in punctuation

**Commas are a partial bottleneck.** On ToyMoodStories, freeze attention patterns so the model cannot redirect attention away from edited commas. Patch attention-head values for the pre-comma phrases while leaving commas unflipped, or patch only the two commas. The interventions reduce logit difference by 38% and 37%, respectively, compared with 75% for the whole phrase including commas. See [Table 1a](../tables/table-1a-comma-vs-phrase.md).

**Distance can increase reliance on summaries.** Insert irrelevant clauses after each preference sentence (e.g. a detail about a character's hat) before asking for their mood. Test value patching at periods versus the preceding phrases. The ratio of logit-difference change rises from 0.29 without filler to 1.15 with 22 intervening tokens: periods can become 15% more important than their phrases in this toy setting. See [Table 1b](../tables/table-1b-period-distance.md) and [semi-separate circuits](../appendix/a4-additional-summarization.md).
