> [返回论文索引](../INDEX.MD) · 附录 D

# 补充实验设置

- **D.1 玩具任务**：训练和评估样本量、位置划分与模型设置见[表 1](../tables/table-1-toy-hyperparameters.md)。
- **D.2 Othello**：每一步在合法走法中随机采样，无合法步用 `pass`，提前结束的棋谱用 `pass` 填至 60。向量 1、−1、0 代表当前选手、对手和空格；归因仅取 16 个中心棋格、每四步一次（第 4 至 56 步）。见[表 2](../tables/table-2-othello-hyperparameters.md)。
- **D.3 TinyStories**：用原 TinyStories tokenizer，spaCy 词级标签分派给组成词的 token。20 个二元句法特征及一个归一化位置特征，在位置 30–39 估计影响，见[表 3](../tables/table-3-text-hyperparameters.md)。
- **D.4 Q(w)**：Gemma-Scope 第 15 层 SAE；从 Neuronpedia 的高激活文本取峰值位置与之后 10 个 token，用编辑距离过滤重复，比较对目标特征的消融前后各位置的 KL。原筛选阈值为平均后续影响小于 0.05。
- **D.5 分类**：用 GPT-4.1-nano 对 GPT-4o-mini 生成的描述判定两类标签：代码/编程语言/数学；句法/文本结构。任一为真即归入形式相关。
- **D.6 导向**：向目标层每个位置的残差流加入 $10w$，温度 1 无条件采样 64 个 20-token 序列。以 Llama 3.1 8B 分类代码片段，另计每段平均标点数。
- **D.7 前瞻**：拟合连接当前位置残差流与冻结语言头的线性映射；以 SVD 右奇异向量取前 $r$ 个方向投影，测 SAE 方向投影余弦与 $Q(w)$ 的关系。

[完整原文附录 D](../../../TeX/Emergent/arXiv-2603.14087v1/full.md#d-additional-experimental-details) · [补充结果](5-further-results.md)
