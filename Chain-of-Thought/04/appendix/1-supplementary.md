> [返回论文索引](../INDEX.MD) · 附录 A–M

# 补充实验、模型训练和输出示例

- **多数选择与预测难度**：多数投票下改变顺序/并行比仍得相似趋势；不依赖真值的 PRM 难度分桶仍需每题 2,048 次采样。[多数](../figures/figure-10-majority.md) · [预测难度与修订](../figures/figure-11-predicted-revisions.md) · [预测难度与搜索](../figures/figure-12-predicted-search.md)
- **PRM 训练**：对软回报用二元交叉熵；AdamW、学习率 $3\times10^{-5}$、batch 128、dropout 0.05、betas (0.9, 0.95)，原训练问题留出 10%，取最低验证损失。逐步取最小、乘积、最后一步三者中最后一步最好。虽用最后一步评分，PRM 仍比 ORM 强，且采样越多差距越明显。[聚合](../figures/figure-13-prm-aggregation.md) · [PRM/ORM](../figures/figure-14-prm-v-orm.md)
- **修订微调**：AdamW、学习率 $10^{-5}$、batch 128、dropout 0、betas (0.9, 0.95)。生成分布和离线验证轨迹不同，作者在离线损失开始上升后选择 checkpoint。基座 PRM 在修订生成上较弱；匹配修订分布的 ORM 更好。加入历史有小幅收益，不加入历史时顺序也优于并行。[验证器消融](../figures/figure-15-revision-verifier.md)
- **ReST-EM**：每题取 64 条最长 5 步轨迹，首次答对即停，平衡长度后再微调；与原修订模型不同，修订轮数增加使表现下降。作者推测在线数据放大了虚假关联。[结果图](../figures/figure-16-rest-em.md)
- **输出样例**：修订样例包括纠正求和、进位制或格式；PRM 样例显示逐步得分，含过度优化时的重复输出。各图见[论文索引](../INDEX.MD)中的「样例图」。

[完整附录 TeX](../../../TeX/Chain-of-Thought/arXiv-2408.03314v1/googledeepmind-test.tex)
