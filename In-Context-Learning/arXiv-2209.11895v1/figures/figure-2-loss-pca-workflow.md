← [论文索引](../INDEX.MD) · [逐 token 损失分析](../methods/3-per-token-loss.md)

# 逐 token 损失的 PCA 流程

![逐 token 损失向量与主成分分析](../images/e9b4a09bdd7b4d5134e4efbee07d357dc8dfce1c63a4896cd7b383fdbcc0ff4d.jpg)

同一批样本中每条序列固定抽一个 token，对每个模型快照形成一条 10,000 维损失向量，再投影到共同计算的前两个主成分。
