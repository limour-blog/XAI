← [论文索引](../INDEX.MD) · [归纳头定义](../methods/2-induction-heads.md)

# 归纳头：前缀匹配并复制后继 token

![归纳头从较早的相同前缀找到后继 token](../images/e7b1d039e15a5f24d5a5bf1976201c712c929054a4adf41d20d1f9707b09a487.jpg)

归纳头找到过去出现的 A，并提高紧跟其后的 B 的 logit。形式为 `[A][B] … [A] → [B]`。
