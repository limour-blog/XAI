> ⬅️ 返回 [论文索引](../INDEX.MD) · §1.1 Sparse Autoencoders

# Sparse autoencoders

The linear representation hypothesis treats meaningful features as directions in activation space. The superposition hypothesis adds that the number of such directions can exceed the dimension of the space. The [toy model study](../../01/INDEX.MD) motivates this hypothesis; the present work tests if sparse dictionary learning can find interpretable directions at production scale.

Let $D$ be the residual stream dimension and $F$ the width of the sparse autoencoder. Apply a scalar normalization so $\mathbb{E}\|\mathbf{x}\|_2^2=D$. The encoder produces nonnegative coefficients and the decoder reconstructs the residual stream:

$$
f_i(\mathbf{x})=\operatorname{ReLU}\big(\mathbf{W}^{\mathrm{enc}}_{i,\cdot}\cdot\mathbf{x}+b_i^{\mathrm{enc}}\big),
$$

$$
\hat{\mathbf{x}}=\mathbf{b}^{\mathrm{dec}}+\sum_{i=1}^{F}f_i(\mathbf{x})\,\mathbf{W}^{\mathrm{dec}}_{\cdot,i}.
$$

The objective combines squared reconstruction error with an L1 penalty on the magnitude of each decoder contribution:

$$
\mathcal L=\mathbb{E}_{\mathbf{x}}\left[\|\mathbf{x}-\hat{\mathbf{x}}\|_2^2+\lambda\sum_i f_i(\mathbf{x})\,\|\mathbf{W}^{\mathrm{dec}}_{\cdot,i}\|_2\right].
$$

A **feature direction** is the unit-normalized decoder column; its **activation** is $f_i(\mathbf{x})\|\mathbf{W}^{\mathrm{dec}}_{\cdot,i}\|_2$. The decoder norm in the penalty prevents reducing the L1 term merely by rescaling a decoder column and inversely rescaling its encoder output. The decomposition is approximate; the reconstruction error is not explained by the dictionary and is retained in [steering experiments](2-dataset-and-steering.md).

Next: [SAE experiments and scaling laws](../results/1-scaling-laws.md).
