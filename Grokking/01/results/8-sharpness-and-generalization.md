⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 A.5 · Generalization measures

# 验证准确率与损失地形尖锐度

在 $S_5$ 置换复合任务中，作者取不同初始化、以相同预算训练的模型，对比验证准确率与极小值的尖锐度估计 $\phi$。两者 Spearman 相关系数是 $-0.79548$，且 $p<0.000014$。结果提示更高验证准确率与更平坦的区域相关；单个任务的相关性不能确定平坦度导致了 grokking。

## 关联章节与图表

- [更多计算能否弥补数据不足？](../discussion/discussion.md)
- [图 7 · 验证准确率与尖锐度](../figures/figure-7-accuracy-and-sharpness.md)
