返回 [论文索引](../INDEX.MD) · 附录

# A. Visualizing the Geometry of Probes

For a linear probe, take the normal of the separating hyperplane. For the nonlinear probes, take the second MLP layer as a linear classifier and apply the same idea. This associates each tile with a vector. The authors display PCA projections and connect vectors for neighboring squares. Relative to the randomized GPT baseline, trained models show more recognizable board geometry. Even the randomized baseline has nonrandom structure, consistent with some board information surviving random projections of move tokens. The paper points to supplementary toggleable 3-D plots.

See [Figure 5](../figures/figure-5-probe-geometry.md).
