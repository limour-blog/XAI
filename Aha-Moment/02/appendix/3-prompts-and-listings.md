> [论文索引](../INDEX.MD) · Supplementary / Training Details / Listings

# 奖励模型提示、冷启动提示与 SFT 样例

**成对有用性评价。** `appendix.tex` 中的 Reward Model Prompt 要求评审先独立作答，再核对两个匿名回答的准确性、有用性、相关性、简洁度与遗漏信息；最终只选一个五级判决（A 明显优于 B / A 略优 / 相当 / B 略优 / B 明显优于 A）。这与用标签作点式安全分类的奖励不同。

| 原始清单 | 用途 |
|---|---|
| [可读解答提示](../../../TeX/Aha-Moment/arXiv-2501.12948v2/data/prompt_summary.md) | 将推理和最终结果整理为更便于理解的解答 |
| [代码题测试数据提示](../../../TeX/Aha-Moment/arXiv-2501.12948v2/data/prompt_code.md) | 为竞赛题产生并筛选测试用例 |
| [简单数学提示](../../../TeX/Aha-Moment/arXiv-2501.12948v2/data/prompt_easy_math.md) | 简单题的简短推理解答示例 |
| [LLM 裁判提示](../../../TeX/Aha-Moment/arXiv-2501.12948v2/data/prompt_lm_judge.md) | 把候选答案与参考答案对照，辅助拒绝采样 |
| [SFT 数学轨迹](../../../TeX/Aha-Moment/arXiv-2501.12948v2/data/sft_sample_math.md) | 数学推理样例 |
| [SFT 编程轨迹](../../../TeX/Aha-Moment/arXiv-2501.12948v2/data/sft_sample_code.md) | 编程推理样例 |
| [SFT 写作轨迹](../../../TeX/Aha-Moment/arXiv-2501.12948v2/data/sft_sample_writing.md) | 非推理样例 |
| [服务风险复核提示](../../../TeX/Aha-Moment/arXiv-2501.12948v2/data/risk_check_prompt.md) | 安全复核用的防护提示 |

[训练数据说明](2-training-details.md) · [安全评估](../results/5-safety.md)
