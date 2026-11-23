> [返回论文索引](../INDEX.MD) · §5 · [图 7](../figures/figure-7-cifar100.md)

# CIFAR100：对重构误差设阈值

单隐层非线性自编码器随瓶颈单元数增加，均方重构误差平滑下降。改用误差低于阈值 $c$ 的样本比例：

$$\operatorname{Reconstruction}_{c}=\frac{1}{n}\sum_{j=1}^{n}\mathbf 1[\|x_j-\hat x_j\|^2<c].$$

在特定 $c$ 下，同一模型家族形成类似 BIG-Bench Periodic Elements 的跃升。这是用度量制造表观跃升的受控例子。[原文](../../../TeX/Emergent/arXiv-2304.15004v2/05_toy_networks.tex)
