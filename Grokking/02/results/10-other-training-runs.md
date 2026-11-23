⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 C.2 · Additional results from different runs

# 种子、样本占比、深度和模数的对照

采用权重衰减且能良好泛化的受分析模型使用傅里叶乘法的某个变体，但没有固定的频率集合。Dropout 模型的嵌入和读出在傅里叶基底上不那么稀疏，尤其是 $p=0.2$ 时对 logits 的余弦拟合较弱。最后一层 MLP 的旁路消融总体保留较高准确率，但部分两层模型有小幅下降。

## 关联章节与图表

- [权重衰减和训练数据量的作用](../results/7-weight-decay.md)
- [Slingshot 不是延迟泛化的必要步骤](../results/12-slingshot.md)
- [不同实验条件下的泛化](../tables/table-6-cross-run-comparisons.md)
- [图 21 · 训练数据比例与收敛步数](../figures/figure-21-steps-to-convergence.md)
- [图 23 · 两层模型的排除损失](../figures/figure-23-two-layer-excluded-loss.md)
- [图 24 · 模 53 加法曲线](../figures/figure-24-mod-53-loss.md)
- [图 25 · 模 401 加法曲线](../figures/figure-25-mod-401-loss.md)
