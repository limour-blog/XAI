返回 [论文索引](../INDEX.MD) · 附录

# A.7. Toy dataset details

## ToyMovieReview

Prompt: `I thought this movie was ADJ, I VRB it. [NEWLINE] Conclusion: This movie is`. Each adjective produces one prompt. The logit difference averages over five positive and five negative completions. Vocabulary as specified in the source:

| Set | Words |
|---|---|
| Positive adjectives, train | perfect, fantastic, delightful, cheerful, good, remarkable, satisfactory, wonderful, nice, fabulous, outstanding, satisfying, awesome, exceptional, adequate, incredible, extraordinary, amazing, decent, lovely, brilliant, charming, terrific, superb, spectacular, great, splendid, beautiful, positive, excellent, pleasant |
| Negative adjectives, train | dreadful, bad, dull, depressing, miserable, tragic, nasty, inferior, horrific, terrible, ugly, disgusting, disastrous, annoying, boring, offensive, frustrating, wretched, inadequate, dire, unpleasant, horrible, disappointing, awful |
| Positive adjectives, test | stunning, impressive, admirable, phenomenal, radiant, glorious, magical, pleasing, lively, warm, strong, helpful, vivid, modern, crisp, sweet |
| Negative adjectives, test | foul, vile, appalling, rotten, grim, dismal, lazy, poor, rough, noisy, sour, flat, ancient, bitter |
| Positive verbs | enjoyed, loved, liked, appreciated, admired |
| Negative verbs | hated, disliked, despised |
| Positive answer tokens | great, amazing, awesome, good, perfect |
| Negative answer tokens | terrible, awful, bad, horrible, disgusting |

## ToyMoodStories

Prompt: `NAME1 VRB1.1 parties, and VRB1.2 them whenever possible. NAME2 VRB2.1 parties, and VRB2.2 them whenever possible. One day, they were invited to a grand gala. QUERYNAME feels very`.

Score `excited` versus `nervous`. The first verb of each subject is `hates` or `loves`; the second is correspondingly `avoids` or `joins`. Subjects always have opposite sentiments. Names: John, Anne, Mark, Mary, Peter, Paul, James, Sarah, Mike, Tom, Carl, Sam, Jack. The dataset includes combinations of `NAME1`, `NAME2`, and `QUERYNAME`, half querying each subject, and sometimes uses the first 16 items for tractability.

See [Section 2.1](../methods/1-datasets-and-models.md).
