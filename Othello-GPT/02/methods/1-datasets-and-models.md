返回 [论文索引](../INDEX.MD) · 方法

# 2.1. Datasets and Models

- **ToyMovieReview:** `I thought this movie was ADJECTIVE, I VERBed it. Conclusion: This movie is`. Adjective and verb agree in sentiment, with 85 adjectives (55 train / 30 test) and 8 verbs. Score the continuation over selected frequent positive and negative descriptors, such as `great` and `terrible`.
- **ToyMoodStory / ToyMoodStories:** `NAME1 VERB1 parties, and VERB2 them whenever possible. NAME2 VERB3 parties, and VERB4 them whenever possible. One day, they were invited to a grand gala. QUERYNAME feels very`. Compare logits for `excited` and `nervous`.
- **Stanford Sentiment Treebank (SST):** 10,662 single-sentence reviews with human annotations for their phrases.
- **OpenWebText (OWT):** source of random text for correlation tests, and GPT-2's pretraining dataset as described in the paper.
- **Models:** GPT-2 and Pythia, decoder-only transformers spanning 85M to 2.8B parameters for the experiments described here. GPT2-small is used for continuation, Pythia-1.4B for classification, Pythia-2.8B for multi-subject tasks.

See [Appendix A.7: exact prompts and vocabulary](../appendix/a7-toy-datasets.md) and [metrics](../appendix/a6-metrics.md).
