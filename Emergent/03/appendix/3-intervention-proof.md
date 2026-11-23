> [返回论文索引](../INDEX.MD) · 附录 C · [Gemma 2](../results/4-gemma-pre-caching.md)

# 命题 5.1：用干预近似预缓存与直接影响比

把方向扰动限制在一个位置和层，比较后续预测分布与紧接 token 预测分布的 KL 变化。下面保留源 Markdown 的局部近似推导。

Proposition C.1 (Restated from Proposition 5.1).

$$
\frac {I _ {i} ^ {k} (\theta^ {/ i} , x \mid w , \theta^ {*} , \nabla_ {\theta} L _ {\mathrm{pre-cached}})}{I _ {i} ^ {k} (\theta^ {/ i} , x \mid w , \theta^ {*} , \nabla_ {\theta} L _ {\mathrm{direct}})} \approx \frac {\sum_ {j > i + 1} d _ {j} ^ {/ i}}{d _ {i + 1} ^ {/ i}} \triangleq Q (w)
$$

Proof. Both direct and pre-cached gradient components consider only the gradient paths that have $r _ { i } ^ { k }$ as a bottleneck, so by chain rule they can be expressed as

$$
\nabla_ {\theta} L _ {i \mathrm{(direct)}} ^ {k} = J _ {\theta} [ r _ {i} ^ {k} ] \cdot \nabla_ {r _ {i} ^ {k}} L _ {i}
$$

And

$$
\nabla_ {\theta} L _ {i (\text { pre - cached })} ^ {k} = J _ {\theta} \left[ r _ {i} ^ {k} \right] \cdot \nabla_ {r _ {i} ^ {k}} \left(\sum_ {j > i} L _ {j}\right)
$$

For convenience, from this point we will treat them together as $\nabla _ { \theta } L _ { c } , c \in$ {direct, pre-cached}.

$$
\begin{array}{r} R (x \mid \theta , \theta^ {*}, w _ {i} ^ {k}) = \frac {1}{2} \left(\langle w _ {i} ^ {k}, r _ {\theta , i} ^ {k} (x) \rangle - \langle w _ {i} ^ {k}, r _ {\theta^ {*}, i} ^ {k} (x) \rangle\right) ^ {2} \\ \nabla_ {\theta} R (x \mid \theta , \theta^ {*}, w _ {i} ^ {k}) = \left(\langle w _ {i} ^ {k}, r _ {\theta , i} ^ {k} (x) \rangle - \langle w _ {i} ^ {k}, r _ {\theta^ {*}, i} ^ {k} (x) \rangle\right) \nabla_ {\theta} \langle w _ {i} ^ {k}, r _ {\theta , i} ^ {k} (x) \rangle = \Delta \cdot J _ {\theta} [ r _ {\theta , i} ^ {k} ] (w _ {i} ^ {k}) \end{array}
$$

Per equation $^ { 8 , }$

(9)

$$
\begin{array}{r} I _ {i} ^ {k} (\theta , x \mid w _ {i} ^ {k}, \theta^ {*}, \nabla_ {\theta} L _ {c}) = \left\langle \nabla_ {\theta} R (x \mid \theta , \theta^ {*}, w _ {i} ^ {k}), \nabla_ {\theta} L _ {c} \right\rangle = \\ = \Delta (w _ {i} ^ {k}) ^ {T} J _ {\theta} [ r _ {\theta , i} ^ {k} ] ^ {T} J _ {\theta} [ r _ {i} ^ {k} ] \cdot \nabla_ {r _ {\theta , i} ^ {k}} L _ {c} = J _ {\theta} [ r _ {\theta , i} ^ {k} ] ^ {T} J _ {\theta} [ r _ {\theta , i} ^ {k} ] \langle \Delta w _ {i} ^ {k}, \nabla_ {r _ {\theta , i} ^ {k}} L _ {c} \rangle \end{array}\tag{10}
$$

Imagine we do a feature ablation: that is, we take a trained model $\theta ^ { * }$ and add a vector $\Delta w _ { i } ^ { k }$ to $r _ { \theta ^ { * } , i } ^ { k } .$ We measure the loss $L _ { c }$ that depends on the model’s output. Doing a first-order approximation around $r _ { \theta ^ { \prime } , i } ( \theta ^ { \prime }$ are the parameters of this intervened model),

$$
L _ {c} ^ {\prime} - L _ {c} ^ {*} \approx (\Delta w _ {i} ^ {k}) ^ {T} \nabla_ {r _ {\theta^ {\prime}, i}} L _ {c}\tag{11}
$$

A corollary of equation 10 and equation 11 is that for any model with parameters $\theta ^ { \prime }$ such that $r _ { \theta , i } ^ { k } = r _ { i \theta ^ { * } } ^ { k } + \Delta \dot { w } _ { i } ^ { k }$ , the influence of component c is proportional to the increase in loss compared to the model $\theta ^ { * }$ .

Assuming that that $\theta ^ { * }$ perfectly fits the data $( p ( x _ { t } \mid x _ { < t } ) = T _ { \theta ^ { * } } ( x _ { t } \mid x _ { < t } )$ , the difference in crossentropy NTP losses becomes

$$
\begin{array}{c} L _ {\text {direct}} ^ {\prime} - L _ {\text {direct}} ^ {*} = - \underset {x _ {t} \sim T _ {\theta^ {*}} (x _ {t} | x _ {<   t})} {\mathbb {E}} \log T _ {\theta^ {\prime}} (x _ {t} \mid x _ {<   t}) + \underset {x _ {t} \sim T _ {\theta^ {*}} (x _ {t} | x _ {<   t})} {\mathbb {E}} \log T _ {\theta^ {*}} (x _ {t} \mid x _ {<   t}) = \\ = \underset {x _ {t} \sim T _ {\theta^ {*}} (x _ {t} | x _ {<   t})} {\mathbb {E}} \frac {\log T _ {\theta^ {*}} (x _ {t} \mid x _ {<   t})}{\log T _ {\theta^ {\prime}} (x _ {t} \mid x _ {<   t})} = D _ {\mathrm{KL}} (T _ {\theta^ {*}} (x _ {t} \mid x _ {<   t}) \| T _ {\theta^ {\prime}} (x _ {t} \mid x _ {<   t})) \end{array}
$$

Similarly, for the pre-cached component, the difference in losses corresponds to the sum of $\mathrm { K L }$ - divergences for future positions.

$$
\frac {I _ {i} ^ {k} (\theta , x \mid w _ {i} ^ {k} , \theta^ {*} , \nabla_ {\theta} L _ {\text {direct}})}{I _ {i} ^ {k} (\theta , x \mid w _ {i} ^ {k} , \theta^ {*} , \nabla_ {\theta} L _ {\text {pre - cached}})} = \frac {D _ {\mathrm{KL}} (T _ {\theta^ {*}} (x _ {i + 1} \mid x _ {\leqslant i}) \| T _ {\theta^ {\prime}} (x _ {i + 1} \mid x _ {\leqslant i})}{\sum_ {j > i + 1} D _ {\mathrm{KL}} (T _ {\theta^ {*}} (x _ {j + 1} \mid x _ {\leqslant j}) \| T _ {\theta^ {\prime}} (x _ {j + 1} \mid x _ {\leqslant j}))}\tag{12}
$$

Where $T _ { \theta ^ { \prime } }$ is a model where $r _ { i } ^ { k }$ was modified along the direction $w _ { i } ^ { k }$
