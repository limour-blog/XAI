> [论文索引](../INDEX.MD) · [R1-Zero 训练分析](../results/1-zero-evolution.md) · [反思词计数图](../figures/supp-reflection.md)

# An “aha moment” of DeepSeek-R1-Zero

**题目：** 若 $a>1$，求方程 $\sqrt{a-\sqrt{a+x}}=x$ 的实数解之和。

**轨迹节选：** 中间检查点的模型先平方、整理到 $x^4-2ax^2-x+(a^2-a)=0$。原表在省略号之后突出显示模型自发写出的句子：

> Wait, wait. Wait. That's an aha moment I can flag here.

模型继续说要重新检查，回到原方程并再次写出 $\sqrt{a+x}=a-x^2$。原表在进一步平方处省略后续，没有展示最终答案；作者用它说明输出中的重新审视现象。
