← [论文索引](../INDEX.MD) · [实验细节](../appendix/12-experimental-details.md)

# 图 16 · 固定训练任务集大小的消融

循环使用同一批 $B$ 个任务而非每步重新采样，单层即使在较小的任务集上仍与 GD 对齐。以下为原图面板。

| $B$ | 训练 | 对齐 | 分布外面板一 | 分布外面板二 |
|---|---|---|---|---|
| 128 | [PDF](../images/cycle/128/train.pdf) | [PDF](../images/cycle/128/sim.pdf) | [PDF](../images/cycle/128/normal_27.pdf) | [PDF](../images/cycle/128/normal_28.pdf) |
| 512 | [PDF](../images/cycle/512/train.pdf) | [PDF](../images/cycle/512/sim.pdf) | [PDF](../images/cycle/512/normal_27.pdf) | [PDF](../images/cycle/512/normal_28.pdf) |
| 2048 | [PDF](../images/cycle/2048/train.pdf) | [PDF](../images/cycle/2048/sim.pdf) | [PDF](../images/cycle/2048/normal_28.pdf) | [PDF](../images/cycle/2048/normal_27.pdf) |
| 8192 | [PDF](../images/cycle/8192/train.pdf) | [PDF](../images/cycle/8192/sim.pdf) | [PDF](../images/cycle/8192/normal_28.pdf) | [PDF](../images/cycle/8192/normal_27.pdf) |
