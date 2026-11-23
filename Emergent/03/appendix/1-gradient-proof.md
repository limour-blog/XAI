> [返回论文索引](../INDEX.MD) · 附录 A · [梯度分解](../methods/2-gradient-decomposition.md)

# 命题 3.1：梯度分解

对每个 $j$ 加减带停梯度项即可将全梯度拆成两部分：经过目标残差流的差值项，与绕过该残差流的停梯度项。经过残差流的部分再按 $j=i$ 与 $j\ne i$ 分为直接和预缓存。下面保留源 Markdown 的推导。

Proposition A.1 (Restated from Proposition 3.1). For any layer k and position i

$$
\nabla_ {\theta} L (x, T _ {\theta} (x)) = \nabla_ {\theta} L _ {i (\text { direct })} ^ {k} (x, T _ {\theta} (x)) + \nabla_ {\theta} L _ {i (\text { pre - cached })} ^ {k} (x, T _ {\theta} (x)) + \nabla_ {\theta} L _ {i (\text { shared })} ^ {k} (x, T _ {\theta} (x))\tag{4}
$$

Where

$$
\nabla_ {\theta} L _ {i \text {(direct)}} ^ {k} (x, T _ {\theta} (x)) = \nabla_ {\theta} L (x _ {i + 1}, T _ {\theta} (x) _ {i}) - \nabla_ {\theta} L \left(x _ {i + 1}, [ T _ {\theta} (x) ] _ {i} ^ {\mathrm{sg} (i, k)}\right),\tag{5}
$$

$$
\nabla_ {\theta} L _ {i \text {(pre - cached)}} ^ {k} (x, T _ {\theta} (x)) = \sum_ {j \neq i} \left[ \nabla_ {\theta} L (x _ {j + 1}, T _ {\theta} (x) _ {j}) - \nabla_ {\theta} L \left(x _ {j + 1}, [ T _ {\theta} (x) ] _ {j} ^ {\mathrm{sg} (i, k)}\right) \right],\tag{6}
$$

$$
\nabla_ {\theta} L _ {i \mathrm{(shared)}} ^ {k} (x, T _ {\theta} (x)) = \sum_ {j} \nabla_ {\theta} L \left(x _ {j + 1}, [ T _ {\theta} (x) ] _ {j} ^ {\mathrm{sg} (i, k)}\right)\tag{7}
$$

Proof.

$$
\nabla_ {\theta} L (x, T _ {\theta} (x)) = \nabla_ {\theta} L (x, T _ {\theta} (x)) + \nabla_ {\theta} L (x, [ T _ {\theta} (x) ] ^ {\operatorname{sg} (i, k)}) - \nabla_ {\theta} L (x, [ T _ {\theta} (x) ] ^ {\operatorname{sg} (i, k)}) =
$$

$$
= \sum_ {j = 1} ^ {N - 1} \nabla_ {\theta} L \left(x _ {j + 1}, [ T _ {\theta} (x) ] _ {j} ^ {\mathrm{sg} (i, k)}\right) + \sum_ {j = 1} ^ {N - 1} \nabla_ {\theta} L \left(x _ {j + 1}, T _ {\theta} (x) _ {j}\right) - \sum_ {j = 1} ^ {N - 1} \nabla_ {\theta} L \left(x _ {j + 1}, [ T _ {\theta} (x) ] _ {j} ^ {\mathrm{sg} (i, k)}\right) =
$$

$$
\begin{array}{c} \overbrace {\sum_ {j = 1} ^ {N - 1} \nabla_ {\theta} L \left(x _ {j + 1} , [ T _ {\theta} (x) ] _ {j} ^ {\mathrm{sg} (i , k)}\right)} ^ {\nabla_ {\theta} L _ {i} ^ {k} (\text {shared})} + \overbrace {\left(\nabla_ {\theta} L \big (x _ {i + 1} , T _ {\theta} (x) _ {i} \big) - \nabla_ {\theta} L \left(x _ {i + 1} , [ T _ {\theta} (x) ] _ {i} ^ {\mathrm{sg} (i , k)}\right)\right)} ^ {\nabla_ {\theta} L _ {i} ^ {k} (\text {direct})} + \\ + \underbrace {\sum_ {j \neq i} \left[ \nabla_ {\theta} L \big (x _ {j + 1} , T _ {\theta} (x) _ {j} \big) - \nabla_ {\theta} L \left(x _ {j + 1} , [ T _ {\theta} (x) ] _ {j} ^ {\mathrm{sg} (i , k)}\right) \right]} _ {\nabla_ {\theta} L _ {i} ^ {k} (\text {pre - cached})} \end{array}
$$
