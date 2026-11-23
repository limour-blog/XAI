# Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters

> [合集索引](../INDEX.MD) · Level 1 · [arXiv:2408.03314v1](https://arxiv.org/abs/2408.03314v1) · [本地主 TeX](../../TeX/Chain-of-Thought/arXiv-2408.03314v1/googledeepmind-test.tex)

## 摘要（Abstract）

Enabling LLMs to improve their outputs by using more test-time computation is a critical step towards building generally self-improving agents that can operate on open-ended natural language. In this paper, we study the scaling of inference-time computation in LLMs, with a focus on answering the question: *if an LLM is allowed to use a fixed but non-trivial amount of inference-time compute, how much can it improve its performance on a challenging prompt?* Answering this question has implications not only on the achievable performance of LLMs, but also on the future of LLM pretraining and how one should tradeoff inference-time and pre-training compute. Despite its importance, little research attempted to understand the scaling behaviors of various test-time inference methods. Moreover, current work largely provides negative results for a number of these strategies. In this work, we analyze two primary mechanisms to scale test-time computation: **(1)** searching against dense, process-based verifier reward models; and **(2)** updating the model's distribution over a response adaptively, given the prompt at test time. We find that in both cases, the effectiveness of different approaches to scaling test-time compute critically varies depending on the difficulty of the prompt. This observation motivates applying a “compute-optimal” scaling strategy, which acts to most effectively allocate test-time compute adaptively per prompt. Using this compute-optimal strategy, we can improve the efficiency of test-time compute scaling by more than **4×** compared to a best-of-N baseline. Additionally, in a FLOPs-matched evaluation, we find that on problems where a smaller base model attains somewhat non-trivial success rates, test-time compute can be used to outperform a **14×** larger model.

## 关键结论

- PaLM 2-S* 在 MATH 上，低预算、中等难度的问题更适合 PRM 束搜索；容易题过度搜索会损害表现。
- 较容易的题倾向于顺序修订；更难的题往往需要兼顾并行探索和局部修订。
- 约 14 倍参数的比较匹配预训练与推理的总 FLOPs，结论随题目难度和推理负载而变；正文评估未计入难度估计开销。

## 章节导航

- [作者与机构](front-matter/authors-affiliations.md) · [元数据](_meta.md) · [引言](introduction/introduction.md)
- [生成器与验证器](methods/1-proposer-and-verifier.md) · [问题设置、预算和难度分桶](methods/2-compute-optimal-policy.md) · [PRM 训练和搜索](methods/3-prm-search.md) · [修订模型与选择](methods/4-revision-model.md)
- [PRM 搜索结果](results/1-verifier-search.md) · [修订结果](results/2-revisions.md) · [FLOPs 匹配比较](results/3-compute-exchange.md)
- 主图：[1 总览](figures/figure-1-overview.md) · [2 搜索方式](figures/figure-2-search-methods.md) · [3 分难度搜索](figures/figure-3-search-difficulty.md) · [4 自适应搜索](figures/figure-4-optimal-search.md) · [5 并行与顺序](figures/figure-5-revision-method.md) · [6 修订轨迹](figures/figure-6-revision-pass1.md) · [7 预算配比](figures/figure-7-revision-ratios.md) · [8 自适应修订](figures/figure-8-optimal-revisions.md) · [9 FLOPs 比较](figures/figure-9-flops.md)
- 附图：[10 多数投票](figures/figure-10-majority.md) · [11 预测难度与修订](figures/figure-11-predicted-revisions.md) · [12 预测难度与搜索](figures/figure-12-predicted-search.md) · [13 PRM 聚合](figures/figure-13-prm-aggregation.md) · [14 PRM 与 ORM](figures/figure-14-prm-v-orm.md) · [15 修订验证器消融](figures/figure-15-revision-verifier.md) · [16 ReST-EM](figures/figure-16-rest-em.md)
- 样例图：[修订 1](figures/figure-17-revision-example-1.md) · [2](figures/figure-18-revision-example-2.md) · [3](figures/figure-19-revision-example-3.md) · [4](figures/figure-20-revision-example-4.md) · [5](figures/figure-21-revision-example-5.md) · [6](figures/figure-22-revision-example-6.md) · [7](figures/figure-23-revision-example-7.md) · [束搜索 1](figures/figure-24-prm-example-1.md) · [2](figures/figure-25-prm-example-2.md) · [3](figures/figure-26-prm-example-3.md) · [4](figures/figure-27-prm-example-4.md) · [5](figures/figure-28-prm-example-5.md) · [6](figures/figure-29-prm-example-6.md)
- [讨论和未来工作](discussion/discussion.md) · [附录实验及样例导读](appendix/1-supplementary.md) · [参考文献](references/references.md)
