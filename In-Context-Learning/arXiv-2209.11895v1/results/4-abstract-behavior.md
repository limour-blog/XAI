← [论文索引](../INDEX.MD)

# Argument 4 · From literal copying to abstract behavior

## Argument 4: Despite being defined narrowly as copying random sequences, induction heads can implement surprisingly abstract types of in-context learning.

STRENGTH OF ARGUMENT FOR SUB-CLAIMS

[查看论据 4 的证据强度表](../tables/table-6-abstract-behavior.md)

All of our previous evidence (in Arguments 1-3) focused on observing or perturbing the connection between induction head formation and macroscopic in-context learning. A totally different angle is to just find examples of induction heads implementing seemingly-difficult in-context learning behaviors; this would make it plausible that induction heads account for the majority of in-context learning. This evidence applies even to the very largest models (and we study up to 12B parameter models), but since it shows only a small number of tasks, it<sup>’</sup>s only suggestive regarding in-context learning in general.

Recall that we define induction heads as heads that empirically copy arbitrary token sequences using a “prefix matching” attention pattern. Our goal is to find heads that meet this definition but <sub>a</sub>l<sub>so</sub> perform more interesting and sophisticated behaviors, essentially showing that induction heads in large models can be “generalizable”.

In this argument, we show some anecdotal examples of induction heads from larger transformers (our 40-layer model with 13 billion parameters) that exhibit exactly such behaviors – namely literal copying, translation, and a specific type of abstract pattern matching. The behaviors are all of the form [A\*][B\*]...[A][B] , aka the “fuzzy nearest neighbor match” or “find something similar early in the sequence and complete the sequence in analogy”. We verify that these heads score highly on our “copying” and “prefix matching” evaluations (that is, they increase the probability of the token they attend to, and attend to tokens where the prefix matches the present token on random text), and are thus “induction heads” by our strict empirical definition, at the same time as they l perform these more sophisticated tasks.

The results of some example heads are shown in the table below, and described in the subsections below.

[查看三个示例归纳头的评分](../tables/table-7-example-heads.md)

## Behavior 1: Literal sequence copying

We'll start with the simplest case of a head that literally copies repeated text, to get familiar with the visualization interface we're using and the basic dynamics of these heads. We've selected an induction head which seems to perform very basic copying behavior and will look at how it behaves on the first paragraph of Harry Potter. We've repeated the first few sentences afterwards to show the head's behavior on longer segments of repeated text. F<sub>or</sub> th<sub>e</sub> f<sub>o</sub>ll<sub>ow</sub>i<sub>ng</sub> i<sub>n</sub>t<sub>erac</sub>ti<sub>ve</sub> <sub>v</sub>i<sub>sua</sub>li<sub>za</sub>ti<sub>ons</sub>, <sub>we recommen</sub>d <sub>v</sub>i<sub>s</sub>iti<sub>ng</sub> th<sub>e</sub> HTML <sub>ar</sub>ti<sub>c</sub>l<sub>e</sub>.

The visualization will show two different things:

In red, "Attention" lets you see where the head is attending to predict the <sub>nex</sub>t token.

In blue, "Logit attr" shows the earlier tokens that contributed to the prediction of the <sub>curren</sub>t token, using "direct-path" logit attribution.<sup>21</sup>

To start exploring the visualization, we suggest you visit the HTML article and try hovering your cursor over the second paragraph.

[查看重复文本上的注意力与直接 logit 归因](../figures/figure-11-literal-copying.md)
Tokens (hover to focus, click to lock)  Selected is source

<EOT>Mr and Mrs Dursley, of number four, Privet Drive, were proud to say that they were perfectly normal, thank you very much. They were the last people you'd expect to be involved in anything strange or mysterious, because they just didn 't hold with such nonsense. Mr Dursley was the director of a firm called G run nings, which made drills. He was a big, beefy man with hardly any neck, although he did have a very large moustache. Mrs Dursley was thin and blonde and had nearly twice the usual amount of neck, which came in very useful as she spent so much of her time craning over garden fences, spying on the neighbours. TheDursleys had a small son called Dudley and in their opinion there was no finer boy anywhere. The Dursleys had everything they wanted, bu they also had a secret, and their greatest fear was that somebody would discover it, They didn 't think they could bear it if anyone found out about the Potters. Mrs Potter was Mrs D ursley's sister, but they hadn 't met for severa vears : in fact, MrsDursley pretended she didn 't have a sister, because her sister and her good- for-nothing husband were as unDursleyish as it was possible to be. TheDursleysshuddered to thinkwhat the neighbours would say if the Potters arrived in the street. The Dursleys knew that the Potters had a small son, too, but they had never even seen him. This boy was another good reason for keepingthe Potters away; they didn't want Dudley mixing with a child like that.

Mr andMrs Dursley,ofnumber four, PrivetDrive, were proud to saythatthey were perfectly normal, thankyou very much. They were thelast people you'd expect to be involved in anything strange or mysterious, because they just didn'thold with such nonsense. MrD ursleywasthe director of a firmcalledGrun nings, which made drills.

If you explore the visualization, you'll see that the head predicts repeating the names "Dursley" and "Potters"; the phrase "a small son”; and then the entire repeated sentences at the end. In all cases, these successful predictions are made by attending back to a previous instance where this phrase was present in the text.

## Behavior 2: Translation

It's a well-known result that language models can translate between languages. Intriguingly, we've encountered many examples of induction heads that can do translation. Here, we explore a head we found in layer 7 of our 40-layer model, showcasing translation between English, French, and German. (As with the others in this section, this head is l an “induction head” by the same definition we<sup>’</sup>ve been using all along, because when shown repeated <sub>ran</sub>d<sub>om</sub> tokens, it uses a “prefix matching” attention pattern to copy the sequence verbatim.)

[查看翻译示例的注意力图组](../figures/figure-12-translation.md)

<EOT>EN: This is the largest temple that I've ever seen. FR: C'est le plus grand temple que j'ai jamais vu DR: Das ist der größte Tempel, den ich je gesehen habe

Note that the overall attention pattern (in red, top left) is more or less an “off-diagonal”, but it meanders a little bit away from a sharp diagonal. The meandering is because different languages have different word order and token lengths. As this head attends sequentially to past tokens that will semantically come next, the attended token position in the earlier sentences jumps around.

The logit attribution patterns for this head are not perfectly sharp; that is, even in cases where the attention head is attending to the matching word in an earlier language, it does not always di<sub>rec</sub>tl<sub>y</sub> increase the logit of the corresponding prediction. We would guess that this is because this head<sup>’</sup>s output needs to be further processed by later layers. However, taken overall, the direct logit attributions show clear evidence of contributing on net to the correct translation.

## Behavior 3: Pattern matching

In this final example, we show an attention head (found at layer 26 of our 40-layer model) which does more complex pattern matching. One might even think of it as learning a simple function in context! (Again, this head <sub>a</sub>l<sub>so</sub> scores highly on our of “basic” induction behaviormeasurements when shown repeated random sequences, so it is an induction head by that definition.)

To explore this behavior, we've generated some synthetic text which follows a simple pattern. Each line follows one of four templates, followed by a label for which template it is drawn from. The template is random selected, as are the words which fill in the template:

(month) (animal): 0

(month) (fruit): 1

(color) (animal): 2

(color) (fruit): 3

Below, we show how the attention head behaves on this synthetic example. To make the diagram easier to read, we've masked the attention pattern to only show the ":" tokens are the destination, and the logit attribution to only show where the output is the integer tokens.

[查看合成分类序列的注意力图组](../figures/figure-13-pattern-matching.md)

Tokens (hover to focus, click to lock)  Selected is source

<EOT>June grape: 1 blue pear:3 July bird:0 gray straw berry: 3 January kiwi:1 purple pineapple:3 September straw berry: 1 March snake:0 April frog:0 purple frog: 2 June lion:0 September lion: 0 March fish: 0 purple snake:2 October monkey: 0 blue cherry:3 July lion: 0 purple straw berry: 3 yellow snake:2 gray pineapple: 3 March fish:0 April lion: 0 green lizard: 2 blue lizard:2 June monkey: 0 yellow kiwi:3 October cherry: 1 yellow lion:2

This head attends back to a previous instance of the correct category more often than not. It often knows to skip over lines where one of the words is identical but the pattern is wrong (such as “January bird” primarily attending to “April fish” and not “grey bird”). This head isn<sup>’</sup>t perfect at this, but empirically it allocates about 65% of its attention from the colons to the correct positions, when tested on a range of similar problems.

## What<sup>’</sup>s going on with more abstract heads that are also induction heads?

We emphasize again that the attention heads that we described above simultaneously implement b<sub>o</sub>th the abstract behaviors that we described, and these <sub>very same</sub> attention heads (as in, the exact same head in the same layer) <sub>a</sub>l<sub>so</sub> satisfy the formal definition of induction head (literal copying of random sequences using prefix matching). The comparison is not a metaphor or a blurring of the definition: induction heads which are d<sub>e</sub>fi<sub>ne</sub>d by their ability to copy literal sequences t<sub>urn ou</sub>t t<sub>o a</sub>l<sub>so</sub> sometimes match more abstract patterns. This is what the table at the beginning of the section shows empirically.

But this still leaves the question: <sub>w</sub>h<sub>y</sub> do the same heads that inductively copy random text also exhibit these other behaviors? One hint is that these behaviors can be seen as “spiritually similar” to copying. Recall that where an induction head is defined as implementing a rule like [A][B] … [A] → [B] , our empirically observed heads also do something like [A\*][B\*] … [A] → [B] where A\* and B\* are similar to A and B in some higher-leve representation. There are several ways these similar behaviors could be connected. For example, note that the first behavior is a special case of the second, so perhaps induction heads are implementing a more general algorithm that reverts to the special case of copying when given a repeated sequence . Another possibility is that induction heads implement literal copying when<sup>22</sup> they take a path through the residual stream that includes only them, but implement more abstract behaviors when they process the outputs of earlier layers that create more abstract representations (such as representations where the same word in English and French are embedded in the same place).

In Argument 5 we<sup>’</sup>ll strengthen this argument by giving a mechanistic account of how induction heads (when doing simple copying with prefix-matching) attend back to the token that comes next in the pattern, and observe that the actual mechanism they use could naturally generalize to more abstract pattern matching. Our point in this section is just that it's actually quite natural for these more abstract induction heads to also exhibit the basic copying behaviors underlying our definition.

