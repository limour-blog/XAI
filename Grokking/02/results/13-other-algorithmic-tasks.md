⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 D.3 · Additional evidence from other algorithmic tasks

# 三个算法任务的有限数据对照

**有限数据对照。** 每步抽取新数据时，以下三项任务没有出现长时间训练—测试分离；改为固定的小训练集后，均可观察到延迟泛化。


五位数加法的逐 token 曲线还有一个细节：即使没有 grokking，不同输出位也可以在不同时间突然改善，总损失可能盖住部分跃升。**相变与延迟泛化不是同义词。**

## 关联章节与图表

- [权重衰减和训练数据量的作用](../results/7-weight-decay.md)
- [每步重采样与固定数据的对照](../tables/table-7-finite-data-tasks.md)
- [图 29 · 五位数加法：每步重采样](../figures/figure-29-five-digit-addition-resampled.md)
- [图 30 · 五位数加法：固定数据](../figures/figure-30-five-digit-addition-fixed-data.md)
- [图 31 · 重复子序列：每步重采样](../figures/figure-31-repeated-subsequences-resampled.md)
- [图 32 · 重复子序列：固定数据](../figures/figure-32-repeated-subsequences-fixed-data.md)
- [图 33 · Skip trigram：每步重采样](../figures/figure-33-skip-trigram-resampled.md)
- [图 34 · Skip trigram：固定数据](../figures/figure-34-skip-trigram-fixed-data.md)
