⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：§2 · Method

# 二元运算任务与评估

每条数据是 $a\circ b=c$。$a$、运算符、$b$、等号、$c$ 各是一个 token，损失和准确率只看答案。对同一运算，随机抽取一定比例的等式作为训练集，其余全部作为验证集。训练和验证共享符号词表，但没有相同的输入对。数字没有十进制表示，置换也没有显式的排列结构；模型只能通过符号之间的关系学运算。

## 关联章节与图表

- [运算范围](../methods/2-binary-operations.md)
- [模型与优化配置](../methods/3-model-and-optimization.md)
- [图 1 · 模除法、学习时间与运算表](../figures/figure-1-delayed-generalization.md)
- [图 5 · 由抽象符号组成的运算表](../figures/figure-5-operation-symbols.md)
