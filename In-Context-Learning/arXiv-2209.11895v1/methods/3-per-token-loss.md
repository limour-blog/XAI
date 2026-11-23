← [论文索引](../INDEX.MD)

# Per-Token Loss Analysis

To better understand how models evolve during training, we analyze what we call the "per-token loss vectors." The core idea traces back to a method used by Erhan <sub>e</sub>t <sub>a</sub>l. , and more generally to[15] the idea of "function spaces" in mathematics.<sup>8</sup>

We start with a collection of models. (In our use, we'll train several different model architectures, saving dozens of “snapshots” of each over the course of training. We<sup>’</sup>ll use this set of snapshots as our collection of models.) Next, we collect the log-likelihoods each model assigns to a consistent set of 10,000 random tokens, each taken from a different example sequence. We combine these log-likelihoods into a "per-token loss vector" and apply Principal Component Analysis (PCA):

Step 1: Run each model / snapshot over the same set of multiple dataset examples, collecting one token's loss per example.

Step 2: For each sample, extract the loss of a consistent token. Combine these to make a vector of losses per model / snapshot.

Step 3: The vectors are jointly reduced with principal component analysis to project them into a shared 2D space.

[查看逐 token 损失的 PCA 流程图](../figures/figure-2-loss-pca-workflow.md)
A more detailed discussion of technical details can be found in the Appendix.

By applying this method to snapshots over training for multiple models, we can visualize and compare how different models' training trajectories evolve in terms of their outputs. Since we're using PCA, each direction can be thought of as a vector of log-likelihoods that models are moving along. We particularly focus on the first two principal components, since we can easily visualize those. Of course, models also move in directions not captured by the first two principal components, but it's a useful visualization for capturing the highest-level story of training.
