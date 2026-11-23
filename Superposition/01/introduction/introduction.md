> ⬅️ 返回 [论文索引](../INDEX.MD) · Introduction

# Introduction

另见 [五特征、二维瓶颈示意](../figures/figure-1-five-features.md) 和 [定义与动机](definitions-and-motivation.md)。下文摘自 [原始 Markdown](../full.md)。

It would be very convenient if the individual neurons of artificial neural networks corresponded to cleanly interpretable features of the input. For example, in an “ideal” ImageNet classifier, each neuron would fire only in the presence of a specific visual feature, such as the color red, a leftfacing curve, or a dog snout. Empirically, in models we have studied, some of the neurons do cleanly map to features. But it isn't always the case that features correspond so cleanly to neurons, especially in large language models where it actually seems rare for neurons to correspond to clean features. This brings up many questions. Why is it that neurons sometimes align with features and sometimes don't? Why do some models and tasks have many of these clean neurons, while they're vanishingly rare in others?

In this paper, we use toy models — small ReLU networks trained on synthetic data with sparse input features — to investigate how and when models represent more features than they have dimensions. We call this phenomenon superposition. When features are sparse, superposition allows compression beyond what a linear model would do, at the cost of "interference" that requires nonlinear filtering.

Consider a toy model where we train an embedding of five features of varying importance in two<sup>1</sup> dimensions, add a ReLU afterwards for filtering, and vary the sparsity of the features. With dense features, the model learns to represent an orthogonal basis of the most important two features (similar to what Principal Component Analysis might give us), and the other three features are not represented. But if we make the features sparse, this changes:

[Illustration: Increasing Feature Sparsity](../figures/figure-1-five-features.md)

This figure and a few others can be reproduced using the toy model framework Colab notebook in our Github repo

Not only can models store additional features in superposition by tolerating some interference, but we'll show that, at least in certain limited cases, <sub>mo</sub>d<sub>e</sub>l<sub>s can per</sub>f<sub>orm compu</sub>t<sub>a</sub>ti<sub>on w</sub>hil<sub>e</sub> i<sub>n</sub> <sub>superpos</sub>iti<sub>on</sub>. (In particular, we'll show that models can put simple circuits computing the absolute value function in superposition.) This leads us to hypothesize that th<sub>e neura</sub>l <sub>ne</sub>t<sub>wor</sub>k<sub>s we o</sub>b<sub>serve</sub> i<sub>n prac</sub>ti<sub>ce are</sub> i<sub>n some sense no</sub>i<sub>s</sub>il<sub>y s</sub>i<sub>mu</sub>l<sub>a</sub>ti<sub>ng</sub> l<sub>arger</sub>, hi<sub>g</sub>hl<sub>y sparse ne</sub>t<sub>wor</sub>k<sub>s</sub>. In other words, it's possible that models we train can be thought of as doing “the same thing as” an imagined muchlarger model, representing the exact same features but with no interference.

Feature superposition isn't a novel idea. A number of previous interpretability papers have speculated about it , and it's very closely related to the long-studied topic of compressed[1, 2] sensing in mathematics , as well as the ideas of distributed, dense, and population codes in[3] neuroscience and deep learning . What, then, is the contribution of this paper?[4] [5]

For interpretability researchers, our main contribution is providing a direct demonstration that superposition occurs in artificial neural networks given a relatively natural setup, suggesting this may also occur in practice. We offer a theory of when and why this occurs, revealing a phase diagram for superposition. We also discover that, at least in our toy model, superposition exhibits complex geometric structure.

But our results may also be of broader interest. We find preliminary evidence that superposition may be linked to adversarial examples and grokking, and might also suggest a theory for the performance of mixture of experts models. More broadly, the toy model we investigate has unexpectedly rich structure, exhibiting phase changes, a geometric structure based on uniform polytopes, "energy level"-like jumps during training, and a phenomenon which is qualitatively similar to the fractional quantum Hall effect in physics. We originally investigated the subject to gain understanding of cleanly-interpretable neurons in larger models, but we've found these toy models to be surprisingly interesting in their own right.

## KEY RESULTS FROM OUR TOY MODELS

In our toy models, we are able to demonstrate that:

Superposition is a real, observed phenomenon.

Both monosemantic and polysemantic neurons can form.

At least some kinds of computation can be performed in superposition.

Whether features are stored in superposition is governed by a phase change.

Superposition organizes features into geometric structures such as digons, triangles, pentagons, and tetrahedrons.

Our toy models are simple ReLU networks, so it seems fair to say that neural networks exhibit these properties in at least some regimes, but it's very unclear what to generalize to real networks.

