⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 D.3 · 中文导读汇总

# 每步重采样与固定数据的对照

| 任务 | 固定样本数 / 模型 | 每步抽新数据 vs. 固定数据 |
| --- | --- | --- |
| 五位数加法 | 700 / 单层完整 Transformer | [逐输出 token 损失](../figures/figure-29-five-digit-addition-resampled.md) · [固定训练集](../figures/figure-30-five-digit-addition-fixed-data.md) |
| 重复子序列预测 | 512 / 两层仅注意力 | [每步抽样](../figures/figure-31-repeated-subsequences-resampled.md) · [固定训练集](../figures/figure-32-repeated-subsequences-fixed-data.md) |
| Skip trigram：输出序列中唯一不小于 10 的 token | 512 / 单层仅注意力 | [每步抽样](../figures/figure-33-skip-trigram-resampled.md) · [固定训练集](../figures/figure-34-skip-trigram-fixed-data.md) |

## 关联章节与图表

- [三个算法任务的有限数据对照](../results/13-other-algorithmic-tasks.md)
- [图 29 · 五位数加法：每步重采样](../figures/figure-29-five-digit-addition-resampled.md)
- [图 30 · 五位数加法：固定数据](../figures/figure-30-five-digit-addition-fixed-data.md)
- [图 31 · 重复子序列：每步重采样](../figures/figure-31-repeated-subsequences-resampled.md)
- [图 32 · 重复子序列：固定数据](../figures/figure-32-repeated-subsequences-fixed-data.md)
- [图 33 · Skip trigram：每步重采样](../figures/figure-33-skip-trigram-resampled.md)
- [图 34 · Skip trigram：固定数据](../figures/figure-34-skip-trigram-fixed-data.md)
