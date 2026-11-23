> [论文索引](../INDEX.MD) · [R1-Zero 奖励](../methods/2-zero-rewards.md)

# Template for DeepSeek-R1-Zero

`prompt` 在训练中替换为具体问题。原表 `tab:r0_template` 的文本：

```text
A conversation between User and Assistant. The user asks a question, and the Assistant solves it.
The assistant first thinks about the reasoning process in the mind and then provides the user with the answer.
The reasoning process and answer are enclosed within <think>...</think> and <answer>...</answer> tags, respectively, i.e., <think> reasoning process here </think> <answer> answer here </answer>.
User: prompt. Assistant:
```
