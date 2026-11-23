⬅️ 返回 [../INDEX.MD](../INDEX.MD) · 所属：附录 B · Why use constructive interference?

# 多个频率如何拉开答案分差？

设 $x=a+b-c$。在模 113 的整数上，任何非零频率 $k$ 对应的 $f_k(x)=\cos(2\pi kx/113)$ 都只在 $x\equiv0\pmod{113}$ 达到 1，但其他候选也可能非常接近 1。举例：$f_{14}(8)\approx0.998$，而 $f_{35}(8)\approx-0.990$。两者相加时，$x=0$ 处相长，$x=8$ 附近的假峰值则被压低。五个频率一起用，可以让正确答案的分数留出更大的余量。

## 关联章节与图表

- [用旋转计算模加法](../methods/2-fourier-multiplication.md)
- [图 8 · 叠加余弦以增强正确答案的峰值](../figures/figure-8-constructive-interference.md)
