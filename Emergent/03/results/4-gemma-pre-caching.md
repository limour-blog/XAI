> [返回论文索引](../INDEX.MD) · §5.1

# Gemma 2：估计终点附近的预缓存程度

以 Gemma-Scope 的 Gemma 2 2B 第 15 层 SAE 为例，在位置 $i$ 把活跃的特征 $w$ 消融为零。令 $d_j^{/i}$ 为原分布相对干预后分布的 KL 散度。命题 5.1 将终点附近的预缓存/直接影响近似为

$$Q(w)=\frac{\sum_{j>i+1}d_j^{/i}}{d_{i+1}^{/i}}.$$

筛掉影响过小的特征后，16,384 个中保留 14,565 个。对代码、数学、句法或结构相关的 SAE 特征，$Q$ 的两端更富集；拟合对数正态得到形式类 $\sigma=1.63\pm0.03$，非形式类 $1.23\pm0.02$（95% 区间）。导向高 $Q$ 特征会使无条件生成中代码和标点增多，低端未显示同样效果。该分析为局部干预，不提供整段训练的影响比。

[图 6](../figures/figure-6-gemma.md) · [图 15](../figures/figure-15-q-distribution.md) · [图 16](../figures/figure-16-formal.md) · [图 17](../figures/figure-17-code-math.md) · [图 18](../figures/figure-18-syntax-structure.md) · [图 19](../figures/figure-19-steering.md) · [表 6](../tables/table-6-log-normal.md) · [表 7](../tables/table-7-low-q.md) · [表 8](../tables/table-8-high-q.md) · [表 9](../tables/table-9-intermediate-q.md)
