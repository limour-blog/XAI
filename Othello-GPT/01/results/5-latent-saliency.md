返回 [论文索引](../INDEX.MD) · 结果

# 5. Latent Saliency Maps: Attribution via Intervention

For a given board and target move, record the predicted probability $p_0$. For each board tile $s$, edit its state with the intervention, measure the new target-move probability $p_s$, and assign saliency $S_s=p_0-p_s$. Center the scores by subtracting the board mean for visualization. The approach attributes effects to a position in the latent board, not to an input token. [Algorithm 1](../methods/5-latent-saliency-algorithm.md) gives the procedure.

The paper visualizes the top-1 move for synthetic and championship models, intervening from $L_s=4$. High saliency in synthetic training concentrates on tiles needed to make the action legal. Championship training highlights legality-related tiles and also more distant or nonessential tiles, consistent with expert moves depending on global board features. The maps do not by themselves identify the exact strategy used by the championship model.

See [Figure 4](../figures/figure-4-latent-saliency.md) and [Appendix E](../appendix/e-saliency-limitations.md).
