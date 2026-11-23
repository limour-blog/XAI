> ⬅️ 返回 [论文索引](../INDEX.MD) · Comments & Replications

# Comments & replications

另见 [复现图 1：损失曲面](../figures/replication-figure-1-loss-surfaces.md)。

## Comments & Replications

I<sub>nsp</sub>i<sub>re</sub>d b<sub>y</sub> th<sub>e or</sub>i<sub>g</sub>i<sub>na</sub>l Ci<sub>rcu</sub>it<sub>s</sub> Th<sub>rea</sub>d <sub>an</sub>d Di<sub>s</sub>till'<sub>s</sub> Di<sub>scuss</sub>i<sub>on</sub> A<sub>r</sub>ti<sub>c</sub>l<sub>e exper</sub>i<sub>men</sub>t, th<sub>e au</sub>th<sub>ors</sub> invited several external researchers who we had previously discussed our preliminary results with to <sub>commen</sub>t <sub>on</sub> thi<sub>s wor</sub>k. Th<sub>e</sub>i<sub>r commen</sub>t<sub>s are</sub> i<sub>nc</sub>l<sub>u</sub>d<sub>e</sub>d b<sub>e</sub>l<sub>ow</sub>.

## REPLICATION & FORTHCOMING PAPER

K<sub>s</sub>hitij S<sub>ac</sub>h<sub>an</sub> i<sub>s</sub> <sub>a</sub> <sub>researc</sub>h i<sub>n</sub>t<sub>ern</sub> <sub>a</sub>t R<sub>e</sub>d<sub>woo</sub>d R<sub>esearc</sub>h.

Redwood Research has been working on toy models of polysemanticity, inspired by Anthropic's work. We plan to separately publish our results, and during our research we replicated many of the experiments in this paper. Specifically, we replicated all plots in the Demonstrating Superposition and Superposition as a Phase Change sections (visualizations of the relu models with different sparsities and the phase diagrams) as well as the plot in The Geometry of Superposition – Uniform Superposition. We found the phase diagrams look quite different depending on the activation function, suggesting that in this toy model some activation functions induce more polysemanticity than others.

Original Authors' Response: Redwood's further analysis of the superposition phase change significantly advanced our own understanding of the issue – we're very excited for their analysis to be shared with the world. We also appreciate the independent replication of our basic results.

## REPLICATION & FURTHER RESULTS

T<sub>om</sub> M<sub>c</sub>G<sub>ra</sub>th i<sub>s</sub> <sub>a</sub> <sub>researc</sub>h <sub>sc</sub>i<sub>en</sub>ti<sub>s</sub>t <sub>a</sub>t D<sub>eep</sub>Mi<sub>n</sub>d.

The results in this paper are an important contribution - they really further our theoretical understanding of a phenomenon that may be central to interpretability research and understanding network representations more generally. It<sup>’</sup>s surprising that such simple settings can produce these rich phenomena. We<sup>’</sup>ve reproduced the experiments in the Demonstrating Superposition and Superposition as a Phase Change sections and have a minor additional result to contribute.

It is possible to exactly solve the expected loss for the $n = 2 , m = 1$ case of the basic ReLU output toy model (ignoring bias terms). The derivation is mathematically simple but somewhat long-winded: the ‘tricks<sup>’</sup> are to (1) represent the sparse portion of the input distribution with delta functions, and (2) replace the ReLu with a restriction of the domain of integration:

$$
\int_ {D} \operatorname{ReLU} (f (x)) d x = \int_ {D \cap f (x) > 0} f (x) d x
$$

Making this substitution renders the integral analytically tractable, which allows us to plot the full loss surface and solve for the loss minima directly. We show some example loss surfaces below:

[Figure 1: Loss surfaces for the $n=2, m=1$ case of the ReLU-output toy model](../figures/replication-figure-1-loss-surfaces.md).

Although many of these loss surfaces (Figure 1a, 1b) have minima qualitatively similar to one of the network weights used in the section Superposition as a Phase Change, we also find a new phase where $\begin{array} { r } { W _ { 1 } \simeq W _ { 2 } \simeq \frac { 1 } { \sqrt { 2 } } ; } \end{array}$ : weights are similar rather than antipodal. This ‘confused feature<sup>’</sup> regime occurs when sparsity is low and both features are important (Figure 1c). (This is slightly similar to the behavior described in The Geometry of Superposition – Collapsing of Correlated Features, but occurs without the features being correlated!) Further, although the solutions we find are often qualitatively similar to the weights used in Superposition as a Phase Change, they can be quantitatively different, as Figure 1a shows. The transition from Figure 1a to Figure 1b is continuous: the minima moves smoothly in weight space as the degree of sparsity alters. This explains the ‘blurry<sup>’</sup> region around the triple point in the phase diagram.

As Figure 1c shows, some combinations of sparsity and relative feature importance lead to loss surfaces with two minima (once the symmetry $( W _ { 1 } , W _ { 2 } )  ( - W _ { 1 } , - W _ { 2 } )$ has been accounted for). If this pattern holds for larger values of and (and we see no reason why itn m would not) this could account for the Discrete "Energy Level" Jumps phenomenon as solutions hop between minima. In some cases (e.g. when parameters approach those needed for a phase transition) the global minimum can have a considerably smaller basin of attraction than local minima. The transition between the antipodal and confused-feature solutions appears to be discontinuous.

Original Authors' Response: This closed form analysis of the $n = 2 , m = 1$ case is fascinating. We hadn't realized that $\begin{array} { r } { W _ { 1 } \simeq W _ { 2 } \simeq \frac { 1 } { \sqrt { 2 } } } \end{array}$ could be a solution without correlated features! The clarification of the "blurry behavior" and the observation about local minima are also very interesting. More generally, we're very grateful for the independent replication of our core results.

## REPLICATION

J<sub>e</sub>ff<sub>rey</sub> W<sub>u</sub> <sub>an</sub>d D<sub>an</sub> M<sub>oss</sub>i<sub>ng</sub> <sub>are</sub> <sub>mem</sub>b<sub>ers</sub> <sub>o</sub>f th<sub>e</sub> Ali<sub>gnmen</sub>t t<sub>eam</sub> <sub>a</sub>t O<sub>pen</sub>AI.

We are very excited about these toy models of polysemanticity. This work sits at a rare intersection of being plausibly very important for training more interpretable models and being very simple and elegant. The results have been surprisingly easy to replicate -- we have reproduced (with very little fuss) plots similar to those in the Demonstrating Superposition – Basic Results, Geometry – Feature Dimensionality, and Learning Dynamics – Discrete "Energy Level" Jumps sections.

Original Authors' Response: We really appreciate this replication of our basic results. Some of our findings were quite surprising to us, and this gives us more confidence that they aren't the result of an idiosyncratic quirk or bug in our implementations.

