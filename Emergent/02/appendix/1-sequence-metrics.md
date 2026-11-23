> [返回论文索引](../INDEX.MD) · 附录 A · [数学模型](../methods/1-analytical-model.md)

# 序列指标的近似行为

对于 $n$ 条长度 $L$ 的序列，逐 token 计数增量是 $1/(nL)$，整串正确率的实际计数增量是 $1/n$。附录用四舍五入到 $1/b$ 网格的记号表示可分辨粒度。若逐 token 错误率为 $\epsilon$，将 token 正确近似为独立且同分布，整串全对约为 $(1-\epsilon)^L$。忽略插入和删除后的替换计数约为 $L\epsilon$（附录编辑距离一段写成 $L(1-\epsilon)$，与其误差率定义及正文不一致）。真实自回归误差存在依赖。

ROUGE-L-Sum 使用 union-LCS。例如候选为 $w_1w_2w_3w_4w_5$，两个参考对应 LCS 为 $w_1w_2$ 和 $w_1w_3w_5$，合并后的长度为 4。原文给出一次仿真，在错误概率由 0.05 增至 0.1 时评分陡降，见[图 9](../figures/figure-9-rouge-l-sum.md)。

[原文附录](../../../TeX/Emergent/arXiv-2304.15004v2/appendix.tex)
