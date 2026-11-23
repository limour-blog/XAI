返回 [论文索引](../INDEX.MD) · 附录

# A.8. Glossary

- **Ablation:** remove a contribution by replacing its output with zeros or a mean. **Mean ablation** uses the mean over a suitable dataset; **directional ablation** edits only a projection.
- **Activation addition / activation steering:** add a vector to the residual stream at selected positions/layers during generation.
- **Activation patching:** replace clean or flipped activations with activations from the other forward pass and measure how output changes.
- **DAS (Distributed Alignment Search):** learn an orthonormal change of basis with gradient descent; the single-direction case patches one dimension and uses a smooth objective such as logit difference.
- **Directional activation patching / directional patching:** replace the projection of an activation along a selected direction, leaving its orthogonal component intact.
- **Logit difference:** difference between completion logits, averaged over completion sets when applicable.
- **OOD / OOS:** out of distribution (a marked distribution shift) / out of sample (distinct test set).
- **Patching metric:** statistic used to assess an activation swap; by default the percentage change in logit difference.
- **Path patching:** patch only the specified paths from senders to receivers and hold other upstream paths fixed.
- **SST:** Stanford Sentiment Treebank.

See [methods](../methods/3-causal-interventions.md) and [metrics](a6-metrics.md).
