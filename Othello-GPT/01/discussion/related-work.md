返回 [论文索引](../INDEX.MD) · 讨论与结论

# 6. Related work

Li, Nye, and Andreas found weak evidence for state encoding in language models fine-tuned on synthetic natural language tasks. Abdou et al. found a geometric relationship between BERT activations and a perceptual color space. Patel and Pavlick grounded spatial and color vocabularies through prompting. These studies concern relatively simple worlds in language.

AlphaZero has access to game structure and rules, though it also learns interpretable strategic concepts. Toshniwal et al. find evidence of board tracking in Transformers trained on chess transcripts but do not characterize the representation itself.

The intervention also relates to plug-and-play steering in autoregressive and diffusion models. Unlike methods that balance fluency and a target attribute via repeated model evaluations, this approach works on internal representations in a single forward pass with optimization steps on activations. TCAV concept attribution uses directional derivatives, which can be seen as a linearization of the gradient-based attribution procedure.

See the [references](../references/references.md).
