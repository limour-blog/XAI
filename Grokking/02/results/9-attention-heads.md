⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 C.1 · Further analysis of the specific training run

# 四个注意力头的角色

等号位置的查询固定，位置 $a$ 与 $b$ 的分数可写成对 token 的查表值加位置常数。忽略微小的自注意力后，权重是两分数之差的 sigmoid。实测中，查表函数接近单频正弦波，而 sigmoid 可较好地用线性函数近似。于是第 $j$ 个头从 `=` 到 $a$ 的注意力权重可拟合为

$$
A_0^j\approx 0.5+\alpha^j[\cos(w_ka)-\cos(w_kb)]+\beta^j[\sin(w_ka)-\sin(w_kb)].
$$


头 0、2 的 OV 输出也分别集中在同一频率，因此权重乘以 OV 输出可以产生单频二次项。头 1、3 的注意力模式近乎互补，OV 输出相近且包含全部五个关键频率；两者相加主要增强残差流中这些频率的一次项。用最佳线性拟合替换 sigmoid 后，测试损失从 $2.41\times10^{-7}$ 略降至 $2.12\times10^{-7}$。

## 关联章节与图表

- [表 2 · 注意力头的正弦与余弦拟合](../tables/table-2-attention-head-fits.md)
- [图 9 · 四个注意力头的周期性模式](../figures/figure-9-attention-patterns.md)
