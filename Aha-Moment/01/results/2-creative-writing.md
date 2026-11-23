> [论文索引](../INDEX.MD) · 第 4.2 节

# Creative Writing

100 个输入各给 4 句随机句子，要求写出连贯的四段文字，依次以指定句子结尾。没有唯一标准答案。GPT-4 对连贯性评分 1–10，每个结果平均 5 次评分；评分标准差跨样本平均约 0.56。部分作者进行盲评，CoT 和 ToT 的展示顺序随机。

零样本 IO 直接写，CoT 先做简短计划，各生成 10 个样本。ToT 先采样 5 个计划、投票 5 次选一个；再基于该计划采样 5 篇、同样投票选一篇。计划是唯一中间步骤，每层仅保留 1 个候选。[流程图](../figures/figure-4-writing-search.md)

[结果图](../figures/figure-5-writing-results.md)中 IO、CoT、ToT 的平均分分别是 6.19、6.93、7.56；人评 ToT 胜 41 对、CoT 胜 21 对、38 对平。迭代改写使 IO 达到 7.67、ToT 达到 7.91。该对照说明写作可通过在计划阶段比较候选或在成稿后修订受益。

[跨模型](../tables/table-6-writing-models.md) · [成本](../tables/table-8-writing-cost.md)
