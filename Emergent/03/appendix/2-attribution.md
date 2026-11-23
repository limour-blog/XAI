> [返回论文索引](../INDEX.MD) · 附录 B · [训练轨迹归因](../methods/4-feature-influence.md)

# 归因算法与 Adam 步长分解

将每个优化器分量投影到特征失配梯度；先训练并拟合特征方向，再复跑得到沿训练路径的归因。下面是源 Markdown 中的细节。

Computing the component influence. By Definition 3.3,

$$
I _ {i} ^ {k} \left(\theta , x \mid w _ {i} ^ {k}, \theta^ {*}, G\right) = \frac {d}{d \varepsilon} R \left(x \mid \theta + \varepsilon G, \theta^ {*}, w _ {i} ^ {k}\right) \Bigg | _ {\varepsilon = 0}
$$

A simple application of the chain rule gives an equivalent definition:

$$
I _ {i} ^ {k} (\theta , x \mid w _ {i} ^ {k}, \theta^ {*}, G) = \left\langle \nabla_ {\theta} R (x \mid \theta , \theta^ {*}, w _ {i} ^ {k}), G \right\rangle\tag{8}
$$

Thus, computing the influence of a given gradient term can be done by taking the inner product of that gradient term and the gradient of the feature mismatch.

To compute $I _ { \mathrm { d i r e c t } } ( w _ { i } ^ { k } , \theta ) , I _ { \mathrm { p r e - c a c h e d } } ( w _ { i } ^ { k } , \theta )$ , and $I _ { \mathrm { s h a r e d } } ( w _ { i } ^ { k } , \theta )$ for given i and $k ,$ we employ the following algorithm. First, we calculate $\nabla _ { \boldsymbol { \theta } } L _ { j }$ for every j in a standard way. Next, we calculate $\nabla _ { \theta } L _ { j } ^ { \mathrm { s g } ( k , i ) }$ in a similar manner, but during the forward pass of the model we detach the tensor corresponding to $r _ { \theta , i } ^ { k } ( x )$ . After that, we compute the gradient decomposition terms according to the definitions in Section 3.4.

The only thing left is the gradient of the feature mismatch. We apply the linear probe defined by $w _ { i } ^ { k }$ to both $r _ { \theta , i } ^ { k } ( x )$ and $r _ { \theta ^ { * } , i } ^ { k } ( x )$ and compute the feature mismatch according to Definition 3.2. We run one more backpropagation to find $\nabla _ { \boldsymbol { \theta } } R$ and take its inner product with the gradient decomposition terms, obtaining the desired influence values.

Correction for Adam. As metioned in Section 3.4, the naive computation of influence components described above is grounded for training with SGD (Remark 3.4) but not for Adam. Indeed, in the case of Adam, the parameter update is computed differently, and a linear step toward the negative gradient no longer reflects how the model is trained. Moreover, due to the inclusion of the first and second moments, the parameter update cannot be computed as a linear sum of three separable components:

$$
\theta_ {t + 1} - \theta_ {t} \neq g (\nabla L _ {\mathrm{(direct)}}) + g (\nabla L _ {\mathrm{(pre-cached)}}) + g (\nabla L _ {\mathrm{(shared)}})
$$

while for SGD it is true, with $g ( x ) = - \eta \cdot x$ (and that fact is the basis behind Remark 3.4).

However, with two small adjustments we can make the Adam parameter update separable. First, we keep separate moments for each of the three components:

$$
m _ {t} ^ {\mathrm{(direct)}} = \beta_ {1} m _ {t - 1} ^ {\mathrm{(direct)}} + (1 - \beta_ {1}) \nabla L _ {\mathrm{(direct)}}
$$

(similarly for the other two).

Second, we use the same adaptive learning rate for all three components:

$$
\alpha = \frac {\eta}{\sqrt {\hat {v} _ {t}} + \epsilon},
$$

where $\hat { v } _ { t }$ is computed normally. Then,

$$
\theta_ {t + 1} - \theta_ {t} = g (m _ {t} ^ {\mathrm{(direct)}}) + g (m _ {t} ^ {\mathrm{(pre-cached)}}) + g (m _ {t} ^ {\mathrm{(shared)}}),
$$

where

$$
g (x) = - \alpha \cdot \frac {x}{1 - \beta_ {1} ^ {t}}.
$$

This way, we can use $g ( m _ { t } ^ { \mathrm { ( d i r e c t ) } } )$ as an adjusted gradient for the direct component. From here, the computation is similar to the case of SGD.

Overall Algorithm. First, for a given dataset, we train a model normally. In all our experiments, we use Adam to follow community standards. After the model has been trained, we freeze it, save the hidden activations on the validation dataset, and obtain a set of linear probes to regress latent variables.

For us, these probes represent the directions $w _ { i } ^ { k }$ needed to compute the gradient-component influence. Once we have the probes, we retrain the model from scratch, fully repeating its training trajectory, which involves starting from the same initialization as the first time, keeping the data point order the same, fixing the PyTorch random seed, etc. During this second training run, at each training batch we compute the feature mismatch and the gradient-component influence for each probe.

The second run is needed because during the first one we do not have the directions $w _ { i } ^ { k }$ needed to compute component influences, and to estimate them we need $\theta ^ { * }$ , which itself requires the training run to finish. In principle, one could save all gradient components during the first run and then retrieve them from memory when computing the influence, but that is extremely expensive in terms of the disk space needed. Thus, we perform two consecutive training runs.
