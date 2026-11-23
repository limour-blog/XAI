> [返回论文索引](../INDEX.MD) · §5 · [图 8](../figures/figure-8-omniglot.md)

# Omniglot：把多张图片绑在一起评分

卷积层嵌入手写字符图像，再把图像嵌入和类别组成的序列送入 decoder-only Transformer。单图正确率随规模上升；将长度 $L=1$ 到 $5$ 的子集改为全对才给 1，较长子集的得分出现类似早期 MMLU 案例的跃升。

[原文](../../../TeX/Emergent/arXiv-2304.15004v2/05_toy_networks.tex) · [LeNet / MNIST 的类似对照](../appendix/2-mnist.md)
