> [返回论文索引](../INDEX.MD) · §4.2

# OthelloGPT：下一步用不到的棋格也能学到

训练 Transformer 在随机生成的 8×8 Othello 棋谱上预测下步，记录最长 60 token；时序棋局的合法走法由棋盘决定。将已占据棋格棋子翻色，如改变下步合法走法集合则为 NTP-useful，否则为 NTP-useless；空格不进入该归因比较。用同一棋格探针对两类样本分别计算失配。

前者的探针相关性更高，差距随深度增大。直接归因在有用棋格为正，对无用棋格不可与零区分；后者仍从预缓存、共享获得正信号。这样解释了世界模型为什么既可读出无用棋格、又没有同等稳健地重建全部棋盘。

[图 3](../figures/figure-3-othello.md) · [表 2](../tables/table-2-othello-hyperparameters.md) · [图 9 训练](../figures/figure-9-othello-training.md) · [图 10 探针](../figures/figure-10-othello-probes.md) · [图 11 中央棋格](../figures/figure-11-othello-inner.md) · [图 12 周边棋格](../figures/figure-12-othello-outer.md)
