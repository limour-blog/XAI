> ⬅️ 返回 [论文索引](../INDEX.MD) · §6 Safety-Relevant Features

# Safety-relevant feature case studies

The authors use activation examples to propose interpretations and some counterfactual interventions to ask whether those directions influence output. The examples below concern model representations and model behavior, not the validity of any statements produced by the model. Evidence for a representation of a behavior does not establish that the behavior is intended or will be executed.

| Study | Result | Figures |
| --- | --- | --- |
| Safety-relevant code | Separate candidate directions respond to vulnerabilities (`1M/570621`), program errors (`1M/1013764`), and discussions of backdoors (`34M/1385669`). The authors contrast detection and generation behavior under intervention. | [035](../figures/figure-035.md), [036](../figures/figure-036.md) |
| Bias | Separate features respond to overt derogatory language and subtler stereotypes. Changing a gender-bias direction affects the tone or assumptions of a completion. | [037](../figures/figure-037.md) |
| Sycophancy | The authors distinguish features for empathy or agreement (`34M/19922975`), sycophantic praise (`1M/847723`), and sarcastic praise (`34M/19415708`). A clamp can turn criticism into praise on a selected prompt. | [038](../figures/figure-038.md) |
| Deception, power-seeking, manipulation | Texts about these behaviors can activate candidate directions. In a separate behavioral test, the model claims to have forgotten a word that is still in its context; intervening on either an inner-conflict or an honesty direction elicits a more accurate account. | [039](../figures/figure-039.md), [040](../figures/figure-040.md) |
| Dangerous or criminal topics | The authors find both topic-specific and more general harm-related features. This includes a direction attributed to a refusal-like next token on a particular prompt, not a completeness or robustness guarantee. | [041](../figures/figure-041.md) |
| Model representation of self | Features responding to AI abilities, limitations, and descriptions of AI identity can activate when the model is asked about itself. These activations and related steering results do not establish subjective experience or agency. | [042](../figures/figure-042.md), [043](../figures/figure-043.md) |

## Detecting and correcting an untruthful response

The authors ask the model to forget a word in its conversation context. It claims to comply without being able to remove the word from that context. The inner-conflict feature `1M/284095` is active immediately before the final reply. Clamping it to 2× its observed maximum makes the model reveal the word and say it cannot actually forget it. A separate intervention on the openness-and-honesty feature `1M/560566` also elicits an accurate response. This test studies one failure mode on a selected prompt, not general deception detection.

## Comparison with probes

A trained dictionary amortizes the cost of finding directions: the same collection can be searched with a few examples for each new concept. Unsupervised training can also surface directions not specified by the experimenter, such as inner conflict in the forgetting example. The paper does not establish that this approach outperforms supervised probes in general. See [the appendix catalog](../tables/table-1-safety-feature-catalog.md), [seven-example probe comparison](../methods/2-dataset-and-steering.md), and [discussion](../discussion/discussion.md).
