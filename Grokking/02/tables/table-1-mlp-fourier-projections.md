⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：§4.2 · 原论文表 1

# 表 1 · MLP 激活在关键读出方向的傅里叶分量

| $W_{L}$ Component | Fourier components of $u_k^T \mathrm{MLP}(a,b)$ or $v_k^T \mathrm{MLP}(a,b)$ | FVE |
| --- | --- | --- |
| $\cos(w_{14} c)$ | $44.6\cos(w_{14}a)\cos(w_{14} b) - 43.6 \sin(w_{14} a) \sin(w_{14} b) \approx 44.1 \cos(w_{14} (a+b))$ | 93.2% |
| $\sin(w_{14} c)$ | $44.1 \sin(w_{14}a)\cos(w_{14} b) + 44.1 \cos(w_{14} a) \sin(w_{14} b) \approx 44.1 \sin(w_{14}(a+b))$ | 93.5% |
| $\cos(w_{35} c)$ | $40.7 \cos(w_{35}a)\cos(w_{35} b) - 43.6 \sin(w_{35} a) \sin(w_{35} b) \approx 42.2 \cos(w_{35} (a+b))$ | 96.8% |
| $\sin(w_{35} c)$ | $41.8 \sin(w_{35}a)\cos(w_{35} b) + 41.8 \cos(w_{35} a) \sin(w_{35} b) \approx 41.8 \sin(w_{35}(a+b))$ | 96.5% |
| $\cos(w_{41} c)$ | $44.8 \cos(w_{41}a)\cos(w_{41} b) - 44.8 \sin(w_{41} a) \sin(w_{41} b) \approx 44.8 \cos(w_{41} (a+b))$ | 97.0% |
| $\sin(w_{41} c)$ | $44.5 \sin(w_{41}a)\cos(w_{41} b) + 44.5 \cos(w_{41} a) \sin(w_{41} b) \approx 44.5 \sin(w_{41}(a+b))$ | 97.0% |
| $\cos(w_{42} c)$ | $64.6 \cos(w_{42}a)\cos(w_{42} b) - 68.5 \sin(w_{42} a) \sin(w_{42} b) \approx 66.6 \cos(w_{42} (a+b))$ | 96.4% |
| $\sin(w_{42} c)$ | $67.8 \sin(w_{42}a)\cos(w_{42} b) + 67.8 \cos(w_{42} a) \sin(w_{42} b) \approx 67.8 \sin(w_{42}(a+b))$ | 96.4% |
| $\cos(w_{52} c)$ | $60.5 \cos(w_{52}a)\cos(w_{52} b) - 65.5 \sin(w_{52} a) \sin(w_{52} b) \approx 63.0 \cos(w_{52} (a+b))$ | 97.4% |
| $\sin(w_{52} c)$ | $64.5 \sin(w_{52}a)\cos(w_{52} b) + 64.5 \cos(w_{52} a) \sin(w_{52} b) \approx 64.5 \sin(w_{52}(a+b))$ | 98.2% |

**表注：** 对每个余弦或正弦方向，先投影 MLP 的激活再做傅里叶变换。中列只列出两个最大的系数；FVE 是用单一和频项替代原投影时的方差解释比例。

## 关联章节与图表

- [读出模型权重里的三角恒等式](../results/3-composing-model-weights.md)
- [图 3 · 嵌入与读出权重的频域分量](../figures/figure-3-embedding-fourier-components.md)
