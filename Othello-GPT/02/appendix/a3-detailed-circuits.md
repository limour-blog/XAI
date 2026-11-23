返回 [论文索引](../INDEX.MD) · 附录

# A.3. Detailed circuit analysis

Set the final residual stream as the initial receiver and patch paths to identify large effects on logit difference. Examine value-weighted or ordinary attention patterns. Recursively patch to the candidate heads as receivers to trace the circuit backwards. Start with GPT-2 and use the smallest larger model that performs a given task when needed.

## A.3.1. Simple sentiment — GPT2-small

A threshold of ≥5% drop in logit difference selects heads 10.4, 9.2, 10.1, and 8.5. The first three attend to `ADJ`/`VRB`; 8.5 attends mainly to the second `movie` token, and 9.2 also attends to it. With those heads as receivers, 7.1 and 7.5 write to `movie` from `ADJ`/`VRB`, causing 7% and 4% shifts respectively when patched. That causal effect is specific to the `SUM` position. Lowering the threshold adds 9.10 (summary reading), 11.9 (direct sentiment reading), and 6.4 (summarizing), giving nine heads in total. See [Figure A.7](../figures/figure-a-7-gpt2-residual-patching.md) and [Figure 7](../figures/figure-7-gpt2-circuit.md).

## A.3.2. Multi-subject mood stories — Pythia-2.8B

In sentiment-flipped prompts, 17.19, 22.5, 14.4, 20.10, and 12.2 have direct effects at `END`. They read the repeated query name (`RNAME`) or `feels` (`FEEL`). At these two destinations the most attended token is often the comma ending the queried preference phrase (`COMMASUM`). Heads 14.4, 20.10, and 12.2 both read the comma to write a summary and read near-end summaries to affect the logits; different layers permit both roles. Head 17.19 instead attends to periods in addition to its primary near-end attention. Head 22.5 mostly attends to `FEEL`. Head 12.17 is the most important dedicated name-summary writer. The upstream comma writers were not fully reverse engineered. See [Figure 8](../figures/figure-8-comma-attention.md) and [Figure A.9](../figures/figure-a-9-comma-path-patching.md).
