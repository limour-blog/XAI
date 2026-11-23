返回 [论文索引](../INDEX.MD) · 方法

# 2.2. Model and Training

The vocabulary has 60 tokens, one for each square other than the four preoccupied central squares. A4 and H6 are the 4th and 58th words, for example. All weights, including the 60 word embeddings, start at random. No geometric prior tells the network that C4 is below B4.

The GPT variant has 8 layers, 8 attention heads, and 512-dimensional hidden activations. Let $y_0,\dots,y_{T-1}$ be a partial game, $x_t^0$ the corresponding embedding, and $x_t^l$ the activation after layer $l$ for token $t$. The causal mask restricts $x_t^l$ to attending to $x_{\leqslant t}^{l-1}$. A linear classifier on $x_{T-1}^8$ predicts logits for the move at $T$. Training minimizes cross-entropy between the true next move and the predicted logits.

See [the legality evaluation](../results/1-legal-moves.md).
