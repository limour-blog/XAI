> [返回论文索引](../INDEX.MD) · 附录 D、F–H

# 输入输出样例与完整提示

原样提示保留在独立源文件中。下表把评估样例与实际用作 in-context demonstrations 的提示分开，避免把测试输出误当作提示。

| 任务 | 输入/输出样例 | 完整提示 |
|---|---|---|
| 算术（非选择题） | [GSM8K 正确](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-gsm8k-correct-examples.tex)、[正确但有瑕疵](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-gsm8k-correct-analysis.tex)、[错误](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-gsm8k-incorrect-examples.tex)、[错误续](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-gsm8k-incorrect-examples-cont.tex) | [主提示 Markdown](3-math-word-problem-prompt.md)、[替代标注一](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-mwp-prompt-alt.tex)、[替代标注二](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-mwp-prompt-alt-b.tex) |
| AQuA | [算术基准示例表](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/math-datasets.tex) | [AQuA](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-aqua-prompt.tex) |
| 末字母拼接 | [输出](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-letter-concat-examples.tex) | [提示](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-letter-concat-prompt.tex) |
| 翻硬币 | [输出](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-coinflip-examples.tex) | [提示](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-coinflip-prompt.tex) |
| CSQA | [输出](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-commonsenseqa-examples.tex) | [提示](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-commonsenseqa-prompt.tex) |
| StrategyQA | [输出](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-strategyqa-examples.tex) | [提示](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-strategyqa-prompt.tex) |
| 日期 | [输出](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-date-understanding-examples.tex) | [提示](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-date-understanding-prompt.tex) |
| 体育 | [输出](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-sports-understanding-examples.tex) | [提示](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-sports-understanding-prompt.tex) |
| SayCan | [输出](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-saycan-examples.tex) | [提示](../../../TeX/Chain-of-Thought/arXiv-2201.11903v6/fables/appendix-saycan-prompt.tex) |

[原始示例图](../figures/figure-3-exemplars.md) · [错误分析](1-faq-and-errors.md)
