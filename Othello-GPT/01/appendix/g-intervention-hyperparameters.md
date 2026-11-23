返回 [论文索引](../INDEX.MD) · 附录

# G. Ablations on Intervention Hyper-parameters

The activation optimization is reported to be robust to choices of optimizer, learning rate $\alpha$, and number of steps. Because all 64 tile states are encoded in the same activation, an edit can change unintended tiles. The regularized loss penalizes departures from the original classifications of non-target tiles:

$$
\sum_{s:B(s)\ne B'(s)}\mathcal L_{\mathrm{CE}}(p_\theta^s(x),B'(s))
+\beta\sum_{s:B(s)=B'(s)}\mathcal L_{\mathrm{CE}}(p_\theta^s(x),B(s)).
$$

The natural benchmark sweep in [Table 3](../tables/table-3-beta-sweep.md) uses $L_s=5$ as stated in Appendix G; there is no clear benefit from the regularization. Starting too early touches layers without reliable world-state information; starting too late leaves too little computation to adapt predictions to the changed board. See [Figure 3](../figures/figure-3-intervention-errors.md) and [Figure 6](../figures/figure-6-probe-capacity.md).
