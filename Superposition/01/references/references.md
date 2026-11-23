> ⬅️ 返回 [论文索引](../INDEX.MD) · References and Footnotes

# References and footnotes

## Footnotes

1 . Where “importance” is a scalar multiplier on mean squared error loss. [↩]

2. In the context of vision, these have ranged from low-level neurons like curve detectors and high-low frequency[6] detectors , to more complex neurons like oriented dog-head detectors or car detectors , to extremely abstract[18] [1] neurons corresponding to famous people, emotions, geographic regions, and more . In language models, researchers[19] have found word embedding directions such as a male-female or singular-plural direction , low-level neurons[8] disambiguating words that occur in multiple languages, much more abstract neurons, and "action" output neurons that help produce certain words . [↩][2]

3. This definition is trickier than it seems. Specifically, something is a feature if there <sub>ex</sub>i<sub>s</sub>t<sub>s</sub> a large enough model size such that it gets a dedicated neuron. This create a kind "epsilon-delta" like definition. Our present understanding – as we'll see in later sections – is that arbitrarily large models can still have a large fraction of their features be in superposition. However, for any given feature, assuming the feature importance curve isn't flat, it should eventually be given a dedicated neuron. This definition can be helpful in saying that something i<sub>s</sub> a feature – curve detectors are a feature because you find them in across a range of models larger than some minimal size – but unhelpful for the much more common case of features we only hypothesize about or observe in superposition. [↩]

4. A famous book by Lakatos illustrates the importance of uncertainty about definitions and how important rethinking[23] definitions often is in the context of research. [↩]

5. This experiment setup could also be viewed as an autoencoder reconstructing . [↩]x

6. A vision model of sufficient generality might benefit from representing every species of plant and animal and every manufactured object which it might potentially see. A language model might benefit from representing each person who has ever been mentioned in writing. These are only scratching the surface of plausible features, but already there seem more than any model has neurons. In fact, large language models demonstrably do in fact know about people of very modest prominence – presumably more such people than they have neurons. This point is a common argument in discussion of the plausibility of "grandmother neurons'' in neuroscience, but seems even stronger for artificial neural networks. [↩]

7. For computational reasons, we won't focus on it in this article, but we often imagine an infinite number of features with importance asymptotically approaching zero. [↩]

8. The choice to have features distributed uniformly is arbitrary. An exponential or power law distribution would also be very natural. [↩]

9. Recall that $\boldsymbol { W } ^ { T } = \boldsymbol { W } ^ { - 1 } \mathrm { ~ i f ~ } \boldsymbol { W }$ is orthonormal. Although $W$ can't be literally orthonormal, our intuition from compressed sensing is that it will be "almost orthonormal" in the sense of Candes & Tao . [↩][25]

1 0. We have the model be $\begin{array} { r } { x ^ { \prime } = W ^ { T } W x , } \end{array}$ but leave Gaussianaly distributed as in Saxe. [↩]x

1 1 . As a brief aside, it's interesting to contrast the linear model interference, $\begin{array} { r } { \sum _ { i \neq j } | W _ { i } \cdot W _ { J } | ^ { 2 } } \end{array}$ , to the notion of coherence in compressed sensing, max<sub>i≠j</sub> $| W _ { i } \cdot W _ { J } |$ . We can see them as the $L ^ { 2 }$ and $L ^ { \infty }$ norms of the same vector. [↩]

1 2. To prove that superposition is never optimal in a linear model, solve for the gradient of the loss being zero or consul Saxe et al. [↩]

1 3. Here, we use “phase change” in the generalized sense of “discontinuous change”, rather than in the more technical sense of a discontinuity arising in the limit of infinite system size. [↩]

1 4. Scaling the importance of all features by the same amount simply scales the loss, and does not change the optimal solutions. [↩]

1 5. Note that there's a degree of freedom for the model in learning $W _ { 1 } { : }$ We can rescale any hidden unit by scaling its row of $W _ { 1 }$ by , and its column ofα $W _ { 2 }$ by , and arrive at the same model. For consistency in the visualization, we rescaleα<sup>−1</sup> each hidden unit before visualizing so that the largest-magnitude weight to that neuron from $W _ { 1 }$ has magnitude . [↩]1

1 6. These specific values were chosen to illustrate the phenomenon we're interested in: the absolute value model learns more easily when there are more neurons, but we wanted to keep the numbers small enough that it could be easily visualized. [↩]

1 7. One question you might ask is whether we can quantify the ability of superposition to enable extra computation by examining the loss. Unfortunately, we can't easily do this. Superposition occurs when we change the task, making i sparser. As a result, the losses of models with different amounts of superposition are not comparable – they're measuring the loss on different tasks! [↩]

1 8. Ultimately we want to say that a model doesn't implement some class of behaviors. Enumerating over all features makes it easy to say a feature doesn't exist (e.g. "there is no 'deceptive behavior' feature") but that isn't quite what we want. We expect models that need to represent the world to represent unsavory behaviors. But it may be possible to build more subtle claims such as "all 'deceptive behavior' features do not participate in circuits X, Y and $Z . "$ [↩]

1 9. Superposition also makes it harder to find interpretable directions in a model without a privileged basis. Without superposition, one could try to do something like the Gram–Schmidt process, progressively identifying interpretable directions and then removing them to make future features easier to identify. But with superposition, one can't simply remove a direction even if one knows that it is a feature direction. [↩]

2 0. More formally, given a matri $H \sim [ d , m ] \ = \ [ h _ { 0 } , h _ { 1 } , \ldots ]$ of hidden layer activations $h \sim [ m ]$ sampled over stimuli, ifd we believe there are underlying features, we can try to find matricesn $A \sim [ d , n ]$ and $B \sim [ n , m ]$ such that isA sparse. [↩]

2 1 . In particular, it seems like we should expect to be able to reduce superposition at least a little bit with essentially no effect on performance, just by doing something like L1 regularization without any architectural changes. Note that models should have a level of superposition where the derivative of loss with respect to the amount of superposition is zero – otherwise, they'd use more or less superposition. As a result, there should be at least some margin within which we can reduce the amount of superposition without affecting model performance. [↩]

2 2. A more subtle issue is that GANs and VAEs often assume that their latent space is Gaussianly distributed. Sparse laten variables are very non-Gaussian, but central limit theorem means that the superposition of many such variables will gradually look more Gaussian. So the latent spaces of some generative models may in fact force models to us superposition! [↩]

2 3. Note that this has a nice information-theoretic interpretation: is the surprisal of a given dimension being non-log(1 − S) zero, and is multiplied by the expected number of non-zeros. [↩]

24. Note that in the compressed sensing case, the phase transition is in the limit as the number of dimensions becomes large - for finite-dimensional spaces, the transition is fast but not discontinuous. [↩]

2 5. We haven<sup>’</sup>t encountered a specific term in the distributed coding literature that corresponds to this hypothesis specifically, although the idea of a “direction in activation-space” is common in the literature, which may be due to ignorance on our part. We call this hypothesis li<sub>near</sub>it<sub>y</sub> [↩]

2 6. Experimental evidence seems to support this [↩][55]

2 7. A related, but different, concept in the neuroscience literature is the “binding problem” in which e.g. a red triangle is[56] a co-occurrence of exactly one shape and exactly one color, which is not a representational challenge, but a binding problem arises if a decomposed code needs to represent simultaneously also a blue square — which shape feature goes with which color feature? Our work does not engage with the binding question, merely treating this as a co-occurrence of “blue”, “red”, “triangle”, and “square”. [↩]

## References

1 . Zoom In: An Introduction to Circuits Olah, C., Cammarata, N., Schubert, L., Goh, G., Petrov, M. and Carter, S., 2020. Distill. DOI: 10.23915/distill.00024.001

2. Softmax Linear Units Elhage, N., Hume, T., Olsson, C., Nanda, N., Henighan, T., Johnston, S., ElShowk, S., Joseph, N., DasSarma, N., Mann, B., Hernandez, D., Askell, A., Ndousse, K., Jones, A., Drain, D., Chen, A., Bai, Y., Ganguli, D., Lovitt, L., Hatfield-Dodds, Z., Kernion, J., Conerly, T., Kravec, S., Fort, S., Kadavath, S., Jacobson, J., Tran-Johnson, E., Kaplan, J., Clark, J., Brown, T., McCandlish, S., Amodei, D. and Olah, C., 2022. Transformer Circuits Thread.

3. Compressed sensing Donoho, D.L., 2006. IEEE Transactions on information theory, Vol 52(4), pp. 1289--1306. IEEE.

4. Local vs. Distributed Coding Thorpe, S.J., 1989. Intellectica, Vol 8, pp. 3--40.

5. Representation learning: A review and new perspectives Bengio, Y., Courville, A. and Vincent, P., 2013. IEEE transactions on pattern analysis and machine intelligence, Vol 35(8), pp. 1798--1828. IEEE.

6. Curve Detectors [link] Cammarata, N., Goh, G., Carter, S., Schubert, L., Petrov, M. and Olah, C., 2020. Distill.

7. Superposition of many models into one Cheung, B., Terekhov, A., Chen, Y., Agrawal, P. and Olshausen, B., 2019. Advances in neural information processing systems, Vol 32.

8. Linguistic regularities in continuous space word representations [PDF] Mikolov, T., Yih, W. and Zweig, G., 2013. Proceedings of the 2013 conference of the north american chapter of the association for computational linguistics: Human language technologies, pp. 746--751.

9. Linguistic regularities in sparse and explicit word representations Levy, O. and Goldberg, Y., 2014. Proceedings of the eighteenth conference on computational natural language learning, pp. 171--180.

1 0. Unsupervised representation learning with deep convolutional generative adversarial networks Radford, A., Metz, L. and Chintala, S., 2015. arXiv preprint arXiv:1511.06434

1 1 . Visualizing and understanding recurrent networks [PDF] Karpathy, A., Johnson, J. and Fei-Fei, L., 2015. arXiv preprint arXiv:1506.02078.

1 2. Learning to generate reviews and discovering sentiment [PDF] Radford, A., Jozefowicz, R. and Sutskever, I., 2017. arXiv preprint arXiv:1704.01444

1 3. Object detectors emerge in deep scene cnns [PDF] Zhou, B., Khosla, A., Lapedriza, A., Oliva, A. and Torralba, A., 2014. arXiv preprint arXiv:1412.6856.

1 4. Network Dissection: Quantifying Interpretability of Deep Visual Representations [PDF] Bau, D., Zhou, B., Khosla, A., Oliva, A. and Torralba, A., 2017. Computer Vision and Pattern Recognition.

1 5. Understanding the role of individual units in a deep neural network Bau, D., Zhu, J., Strobelt, H., Lapedriza, A., Zhou, B. and Torralba, A., 2020. Proceedings of the National Academy of Sciences, Vol 117(48), pp. 30071--30078. National Acad Sciences.

1 6. On the importance of single directions for generalization [PDF] Morcos, A.S., Barrett, D.G., Rabinowitz, N.C. and Botvinick, M., 2018. arXiv preprint arXiv:1803.06959

1 7. On Interpretability and Feature Representations: An Analysis of the Sentiment Neuron Donnelly, J. and Roegiest, A., 2019. European Conference on Information Retrieval, pp. 795--802.

1 8. High-Low Frequency Detectors Schubert, L., Voss, C., Cammarata, N., Goh, G. and Olah, C., 2021. Distill. DOI: 10.23915/distill.00024.005

1 9. Multimodal Neurons in Artificial Neural Network Goh, G., Cammarata, N., Voss, C., Carter, S., Petrov, M., Schubert, L., Radford, A. and Olah, C., 2021. Distill. DOI: 10.23915/distill.00030

2 0. Convergent learning: Do different neural networks learn the same representations? Li, Y., Yosinski, J., Clune, J., Lipson, H., Hopcroft, J.E. and others,, 2015. FE@ NIPS, pp. 196--212.

2 1 . Feature Visualization [link] Olah, C., Mordvintsev, A. and Schubert, L., 2017. Distill. DOI: 10.23915/distill.00007

2 2. Adversarial examples are not bugs, they are features Ilyas, A., Santurkar, S., Tsipras, D., Engstrom, L., Tran, B. and Madry, A., 2019. Advances in neural information processing systems, Vol 32.

2 3. Proofs and refutations Lakatos, I., 1963. Nelson London.

24. Sparse coding with an overcomplete basis set: A strategy employed by V1? Olshausen, B.A. and Field, D.J., 1997. Vision research, Vol 37(23), pp. 3311--3325. Elsevier.

2 5. Decoding by linear programming Candes, E.J. and Tao, T., 2005. IEEE transactions on information theory, Vol 51(12), pp. 4203--4215. IEEE.

2 6. Exact solutions to the nonlinear dynamics of learning in deep linear neural networks Saxe, A.M., McClelland, J.L. and Ganguli, S., 2014.

2 7. In-context Learning and Induction Heads [HTML] Olsson, C., Elhage, N., Nanda, N., Joseph, N., DasSarma, N., Henighan, T., Mann, B., Askell, A., Bai, Y., Chen, A., Conerly T., Drain, D., Ganguli, D., Hatfield-Dodds, Z., Hernandez, D., Johnston, S., Jones, A., Kernion, J., Lovitt, L., Ndousse, K., Amodei, D., Brown, T., Clark, J., Kaplan, J., McCandlish, S. and Olah, C., 2022. Transformer Circuits Thread.

2 8. A Mechanistic Interpretability Analysis of Grokking [link] Nanda, N. and Lieberum, T., 2022.

2 9. Grokking: Generalization beyond overfitting on small algorithmic datasets Power, A., Burda, Y., Edwards, H., Babuschkin, I. and Misra, V., 2022. arXiv preprint arXiv:2201.02177.

30. The surprising simplicity of the early-time learning dynamics of neural networks Hu, W., Xiao, L., Adlam, B. and Pennington, J., 2020. Advances in Neural Information Processing Systems, Vol 33, pp. 17116--17128.

3 1 . A mathematical theory of semantic development in deep neural networks Saxe, A.M., McClelland, J.L. and Ganguli, S., 2019. Proceedings of the National Academy of Sciences, Vol 116(23), pp. 11537--11546. National Acad Sciences.

3 2. Towards the science of security and privacy in machine learning Papernot, N., McDaniel, P., Sinha, A. and Wellman, M., 2016. arXiv preprint arXiv:1611.03814.

3 3. Adversarial spheres Gilmer, J., Metz, L., Faghri, F., Schoenholz, S.S., Raghu, M., Wattenberg, M. and Goodfellow, I., 2018. arXiv preprint arXiv:1801.02774.

34. Adversarial robustness as a prior for learned representations Engstrom, L., Ilyas, A., Santurkar, S., Tsipras, D., Tran, B. and Madry, A., 2019. arXiv preprint arXiv:1906.00945.

3 5. Delving into transferable adversarial examples and black-box attacks Liu, Y., Chen, X., Liu, C. and Song, D., 2016. arXiv preprint arXiv:1611.02770.

36. An introduction to systems biology: design principles of biological circuits Alon, U., 2019. CRC press. DOI: 10.1201/9781420011432

37. The Building Blocks of Interpretability [link] Olah, C., Satyanarayan, A., Johnson, I., Carter, S., Schubert, L., Ye, K. and Mordvintsev, A., 2018. Distill. DOI: 10.23915/distill.00010

3 8. Visualizing Weights [link] Voss, C., Cammarata, N., Goh, G., Petrov, M., Schubert, L., Egan, B., Lim, S.K. and Olah, C., 2021. Distill. DOI: 10.23915/distill.00024.007

39. A Review of Sparse Expert Models in Deep Learning Fedus, W., Dean, J. and Zoph, B., 2022. arXiv preprint arXiv:2209.01667.

40. A Mathematical Framework for Transformer Circuits [HTML] Elhage, N., Nanda, N., Olsson, C., Henighan, T., Joseph, N., Mann, B., Askell, A., Bai, Y., Chen, A., Conerly, T., DasSarma, N., Drain, D., Ganguli, D., Hatfield-Dodds, Z., Hernandez, D., Jones, A., Kernion, J., Lovitt, L., Ndousse, K., Amodei, D., Brown, T., Clark, J., Kaplan, J., McCandlish, S. and Olah, C., 2021. Transformer Circuits Thread.

4 1 . An Overview of Early Vision in InceptionV1 Olah, C., Cammarata, N., Schubert, L., Goh, G., Petrov, M. and Carter, S., 2020. Distill. DOI: 10.23915/distill.00024.002

4 2. beta-vae: Learning basic visual concepts with a constrained variational framework Higgins, I., Matthey, L., Pal, A., Burgess, C., Glorot, X., Botvinick, M., Mohamed, S. and Lerchner, A., 2016.

43. Infogan: Interpretable representation learning by information maximizing generative adversarial nets Chen, X., Duan, Y., Houthooft, R., Schulman, J., Sutskever, I. and Abbeel, P., 2016. Advances in neural information processing systems, Vol 29.

44. Disentangling by factorising Kim, H. and Mnih, A., 2018. International Conference on Machine Learning, pp. 2649--2658.

45. Uncertainty principles and ideal atomic decomposition Donoho, D.L., Huo, X. and others,, 2001. IEEE transactions on information theory, Vol 47(7), pp. 2845--2862. Citeseer.

46. Compressed sensing and best k-term approximation Cohen, A., Dahmen, W. and DeVore, R., 2009. Journal of the American mathematical society, Vol 22(1), pp. 211--231.

47. A remark on compressed sensing Kashin, B.S. and Temlyakov, V.N., 2007. Mathematical notes, Vol 82(5), pp. 748--755. Springer.

48. Information-theoretic bounds on sparsity recovery in the high-dimensional and noisy setting Wainwright, M., 2007. 2007 IEEE International Symposium on Information Theory, pp. 961--965.

49. Lower bounds for sparse recovery Do Ba, K., Indyk, P., Price, E. and Woodruff, D.P., 2010. Proceedings of the twenty-first annual ACM-SIAM symposium on Discrete Algorithms, pp. 1190--1197.

50. Neighborly polytopes and sparse solution of underdetermined linear equations Donoho, D.L., 2005.

5 1 . Compressed sensing: How sharp is the RIP Blanchard, J.D., Cartis, C. and Tanner, J., 2009. SIAM Rev., accepted, Vol 10, pp. 090748160.

5 2. A deep learning approach to structured signal recovery Mousavi, A., Patel, A.B. and Baraniuk, R.G., 2015. 2015 53rd annual allerton conference on communication, control, and computing (Allerton), pp. 1336--1343.

53. Learned D-AMP: Principled neural network based compressive image recovery Metzler, C., Mousavi, A. and Baraniuk, R., 2017. Advances in Neural Information Processing Systems, Vol 30.

54. Compressed Sensing using Generative Models [HTML] Bora, A., Jalal, A., Price, E. and Dimakis, A.G., 2017. Proceedings of the 34th International Conference on Machine Learning, Vol 70, pp. 537--546. PMLR.

5 5. Average firing rate rather than temporal pattern determines metabolic cost of activity in thalamocortical relay neurons Yi, G. and Grill, W., 2019. Scientific reports, Vol 9(1), pp. 6940. DOI: 10.1038/s41598-019-43460-8

56. Distributed representations Plate, T., 2003. Cognitive Science, pp. 1-15.

57. Compressed Sensing, Sparsity, and Dimensionality in Neuronal Information Processing and Data Analysis [link] Ganguli, S. and Sompolinsky, H., 2012. Annual Review of Neuroscience, Vol 35(1), pp. 485-508. DOI: 10.1146/annurevneuro-062111-150410

