> [返回论文索引](../INDEX.MD) · §3–4

# 按难度与预算选策略

给定问题 $q$、生成预算 $N$、候选超参数 $\theta$，定义策略诱导的分布 $\operatorname{Target}(\theta,N,q)$，目标是最大化从该分布采到正确答案的概率：

$$\theta^*(q,N)=\arg\max_\theta\;\mathbb E_{y\sim\operatorname{Target}(\theta,N,q)}[\mathbf 1(y=y^*(q))].$$

实验用 PaLM 2-S*（Codey）和 MATH 的约 12,000 训练题、500 测试题划分。对每题采样 2,048 次，将基座 pass@1 的估计分成五个分位桶（1 易、5 难）。**Oracle 难度**依赖答案判定，**预测难度**以同批样本的 PRM 最终分数均值取代正确率。每个桶做两折交叉评估：一折选策略，另一折测，交换后取平均。

难度是相对于基座模型的，不是 MATH 的人工难度标签。预测难度不需要标准答案，但采样估计本身昂贵，论文预算比较未计入这一项。

[搜索结果](../results/1-verifier-search.md) · [修订结果](../results/2-revisions.md) · [预测难度附录](../appendix/1-supplementary.md)
