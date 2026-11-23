⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：§1 · Introduction

# 把泛化变成填运算表

让 Transformer 看一张**只填了一部分的运算表**。输入是两个抽象符号，目标是预测它们的运算结果。模型可以先把已知格子背下来，长时间填不出空白格子，之后才学会对几乎所有未见组合给出正确结果。论文把这种延迟泛化称为 grokking。

## 关联章节与图表

- [图 1 · 模除法、学习时间与运算表](../figures/figure-1-delayed-generalization.md)
