> [返回论文索引](../INDEX.MD) · §4.1

# Majority 与 Conditioned Majority

两项任务前 10 个 token 是均匀随机的，后 10 个从一个集合取样。Majority 的输出集合是前段最频繁的 token；Conditioned Majority 是前段最频繁跟在 A 之后的 token。后者可用两层结构，先认出前一 token，再聚合 A 之后的位置。前段不需要相关特征来预测自身的下一个随机 token。

[图 2](../figures/figure-2-toy-probes.md)的联合消融使前段探针最弱；恢复预缓存或共享可改善探针。两种 myopic 模型都不能完整学会 Conditioned Majority（输出首位约 0.76），非 myopic 为 0.99 或 1.00。[图 8](../figures/figure-8-toy-influence.md)中，Majority 输入段以共享为主，到位置 10 时转向直接；Conditioned Majority 的非共享模型在前段的预缓存贡献更清楚。

[表 1：超参数](../tables/table-1-toy-hyperparameters.md) · [表 4：输出阶段准确率](../tables/table-4-toy-accuracy.md)
