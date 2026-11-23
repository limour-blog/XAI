← [论文索引](../INDEX.MD) · [分布外设置](../appendix/2-ood.md) · [多层结果](../results/2-multiple-layers.md)

# 图 6 · 改变输入分布与教师尺度

| 模型 | 输入范围 | 教师尺度 | 未见输入分布 | 未见分布下的教师尺度 |
|---|---|---|---|---|
| 单层 | [PDF](../images/linear/linear_one_layer_one_head_0_002/normal.pdf) | [PDF](../images/linear/linear_one_layer_one_head_0_002/normal_6.pdf) | [PDF](../images/linear/linear_one_layer_one_head_0_002/normal_5.pdf) | [PDF](../images/linear/linear_one_layer_one_head_0_002/ood_3.pdf) |
| 两层循环 | [PDF](../images/linear/two_layers_rec/normal_11.pdf) | [PDF](../images/linear/two_layers_rec/normal_13.pdf) | [PDF](../images/linear/two_layers_rec/normal_12.pdf) | [PDF](../images/linear/two_layers_rec/ood_8.pdf) |
| 五层 | [PDF](../images/linear/linear_five_layer/normal_13.pdf) | [PDF](../images/linear/linear_five_layer/normal_11.pdf) | [PDF](../images/linear/linear_five_layer/normal_12.pdf) | [PDF](../images/linear/linear_five_layer/ood_9.pdf) |

循环模型与 GD++ 的匹配较好，五层非循环模型远离训练条件时匹配变差。
