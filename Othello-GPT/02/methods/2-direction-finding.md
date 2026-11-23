返回 [论文索引](../INDEX.MD) · 方法

# 2.2. Finding Directions

Let $\mathcal P$ and $\mathcal N$ be positive and negative ToyMovieReview inputs. For $x$ in either set, $\mathbf a_x^L$ and $\mathbf v_x^L$ denote the residual-stream vector at layer $L$ at the adjective and verb respectively. The verb vectors are held out. Let $p$ and $n$ denote the positive and negative completions.

| Method | Direction estimate |
|---|---|
| Mean Difference (MD) | Positive mean minus negative mean, $\frac{1}{\lvert\mathcal P\rvert}\sum_{x\in\mathcal P}\mathbf a_x^L-\frac{1}{\lvert\mathcal N\rvert}\sum_{x\in\mathcal N}\mathbf a_x^L$ (the norms of the sets denote their counts). |
| $K$-means (KM) | Centroid difference $\mathbf c_1-\mathbf c_0$ from two clusters fitted to the adjective vectors. |
| Linear Probing (LR) | Normalized logistic-regression weights, $\mathbf w/\lVert\mathbf w\rVert$, where the model predicts $1/(1+\exp(-\mathbf w\cdot\mathbf a_x^L))$. |
| Distributed Alignment Search (DAS) | Learn a direction $\theta$ using an objective based on the logit difference after directional patching. |
| Principal Component Analysis (PCA) | First principal component of the adjective vectors. |

The DAS objective in the paper is written as:

$$
\sum_{x\in\mathcal P}[\operatorname{logit}_\theta(x;p)-\operatorname{logit}_\theta(x;n)]
+\sum_{x\in\mathcal N}[\operatorname{logit}_\theta(x;n)-\operatorname{logit}_\theta(x;p)].
$$

See [Figure 2](../figures/figure-2-direction-similarities.md), [causal methods](3-causal-interventions.md), [direction comparison](../results/1-direction-comparison.md), and the [DAS dimension sweep](../appendix/a2-das-dimensions.md).
