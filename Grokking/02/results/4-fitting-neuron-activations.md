⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：§4.3 · Zooming in: approximating neurons with sines and cosines

# 用单频二次多项式拟合神经元

**单元与频率对得上。** 512 个 MLP 神经元中有 433 个，用单一频率的正弦、余弦二次多项式就能解释超过 85% 的激活方差。按最佳频率把这些神经元分组后，每组对输出的贡献也集中在对应频率。主实验的四个注意力头里，两个近似做单频二次计算，另外两个主要放大关键频率信号。

## 关联章节与图表

- [图 4 · 注意力分数、MLP 激活与 logits 的周期性](../figures/figure-4-periodicity-of-activations.md)
- [图 5 · 神经元的频率拟合及对 logits 的贡献](../figures/figure-5-neuron-frequency-fits.md)
- [图 12 · 其他 MLP 神经元的周期性激活](../figures/figure-12-additional-neuron-activations.md)
