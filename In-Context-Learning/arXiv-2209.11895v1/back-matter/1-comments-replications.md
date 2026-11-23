← [论文索引](../INDEX.MD)

# Comments, Replications & Change Log


I<sub>nsp</sub>i<sub>re</sub>d b<sub>y</sub> th<sub>e or</sub>i<sub>g</sub>i<sub>na</sub>l Ci<sub>rcu</sub>it<sub>s</sub> Th<sub>rea</sub>d <sub>an</sub>d Di<sub>s</sub>till'<sub>s</sub> Di<sub>scuss</sub>i<sub>on</sub> A<sub>r</sub>ti<sub>c</sub>l<sub>e exper</sub>i<sub>men</sub>t, th<sub>e au</sub>th<sub>ors</sub> invited several external researchers who were also investigating induction heads to comment on thi<sub>s wor</sub>k. Th<sub>e</sub>i<sub>r commen</sub>t<sub>s are</sub> i<sub>nc</sub>l<sub>u</sub>d<sub>e</sub>d b<sub>e</sub>l<sub>ow</sub>.

## REPLICATION

Ad<sub>am</sub> S<sub>c</sub>h<sub>er</sub>li<sub>s</sub> i<sub>s a researc</sub>h<sub>er a</sub>t R<sub>e</sub>d<sub>woo</sub>d R<sub>esearc</sub>h.

Redwood Research has been working on language model interpretability, inspired in part by Anthropic<sup>’</sup>s work. We<sup>’</sup>ve found induction heads reliably appearing in two-layer attention-only transformers. Their structure roughly matches the description in “Analyzing a Two-Layer Model” from Anthropic<sup>’</sup>s previous paper, with previous-token heads in layer 0 and induction heads in layer 1 (often one of each). These each have the expected attention behaviors. We tested this by replacing attention-score matrices with idealized versions and comparing the change in loss to the change from ablating that head. Replacing the previous-token head<sup>’</sup>s scores with exact previous-token attention recovered 99% of the loss difference. Replacing the induction head<sup>’</sup>s scores with a simple approximation (attending to the first token and to exact [A][B]...[A] matches) recovered about 65% of the loss difference. Our induction heads also match patterns of the form [A][B][C]...[A][B]→[C] ; including this in the substituted attention scores recovered an additional 10% of loss difference. The induction head<sup>’</sup>s OV circuit copies tokens, including some fuzzy matching of semantically similar tokens. Its QK circuit is dominated by K-composition with the previous-token head; the previous-token head<sup>’</sup>s OV matrix copies information to a new subspace and the induction head<sup>’</sup>s QK matrix copies it back to the usual token embedding. We<sup>’</sup>ve also cataloged a few other kinds of attention heads, including skip-trigram heads.

## REPLICATION

T<sub>om</sub> Li<sub>e</sub>b<sub>erum</sub> i<sub>s</sub> <sub>a</sub> <sub>mas</sub>t<sub>er</sub>'<sub>s</sub> <sub>s</sub>t<sub>u</sub>d<sub>en</sub>t <sub>a</sub>t th<sub>e</sub> U<sub>n</sub>i<sub>vers</sub>it<sub>y</sub> <sub>o</sub>f A<sub>ms</sub>t<sub>er</sub>d<sub>am</sub>.

I used the empirical criterion for induction heads presented in this paper to look for induction heads in publicly available models. To reiterate: on a sequence of tokens

[A][B] .... [A] → [B] , a head is called an induction head if it attends to the previous

[B] when reading the last [A] , and if the previous [B] increased the logit of the last [B] .

Under this definition, I found potential induction heads in GPT2 and GPT-Neo mostly starting in the mid-depth region. I made an interactive version to explore attention and logit attribution across all layers and heads on the long Harry Potter prompt with the repetition of the first paragraph. It can be accessed here. For example, for GPT2-XL, head 20 in layer 21 seems to be an induction head, as well as head 0 in layer 12 of GPT-Neo-2.7B. For these heads we can see that virtually every token in the repetition of the first paragraph attends to its following token in the original paragraph. Thanks to EleutherAI for providing the compute resources for this project.

At one point the paper speculates on the minimal context length necessary to form induction heads. On a synthetic dataset, I have already found induction to be easily learned with a context length of 4. However, I believe that this is, in general, a property of the dataset/data distribution rather than the model itself, i.e. "how useful is induction for this task, on this dataset?". While it is intriguing to think about the statistics of language in this way, I am not sure how useful this line of research would be to the overall project of interpretability.

## Change Log

The following changes have been made after publication:

2022-09-20: Corrects the definition of Prefix matching in two places, which incorrectly stated “tokens that were <sub>prece</sub>d<sub>e</sub>d by the current token” instead of “preceded” or “were f<sub>o</sub>ll<sub>owe</sub>d by”. Adds detail to the definition of the copying head evaluator to explain that the effect on “raising the logits” is calculated using a ReLU

