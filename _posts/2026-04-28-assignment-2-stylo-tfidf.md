---
layout: post
title: "Assignment 2 - Style vs Content: Comparing Stylo and TF-IDF in a Science Fiction Corpus"
date: 2026-04-28
categories: [Assignment-2]
tags: [ScienceFiction, ProjectGutenberg, Stylo, TFIDF, DistantReading, Stylometry]
---
## Introduction

This project compares two computational methods, Stylo and TF-IDF, using a corpus of eighteen science fiction texts from Project Gutenberg. The authors include Leigh Brackett, Philip K. Dick, Henry Kuttner, Andre Norton, H. G. Wells, and Marion Zimmer Bradley.

I wanted to see whether these two methods would tell the same story about the corpus. They did not exactly do that. Instead, they showed two different layers of the same texts. Stylo was better at showing patterns of writing style, while TF-IDF was better at showing patterns of content and theme.

So my main argument is simple: **Stylo shows how authors write, while TF-IDF shows what they write about.**

---

## Stylometry: Looking for Style

Stylo works with most frequent words, or MFWs. These are often common words like “the,” “and,” “of,” and “to.” These words do not seem meaningful at first, but they can reveal habits in an author’s style. Writers often use these small words unconsciously, so stylometry can help detect patterns of authorship.

### Cluster Analysis: 100 MFW

![Stylo Cluster Analysis 100 MFW](https://erazeerhead04.github.io/rlac/assets/images/stylo-100mfw.png)

At 100 MFW, the cluster analysis already shows some strong author patterns. Philip K. Dick’s texts cluster closely together. Andre Norton’s texts also form a clear group. This suggests that Stylo is successfully detecting authorial style.

However, the results are not perfectly clean. Brackett, Kuttner, and Zimmer Bradley overlap more. I do not think this is a failure of the method. Instead, it shows that these authors share some broader pulp science fiction conventions. Their stories may have different plots, but they come from related genre traditions.

---

### Cluster Analysis: 500 MFW

![Stylo Cluster Analysis 500 MFW](https://erazeerhead04.github.io/rlac/assets/images/stylo-500mfw.png)

At 500 MFW, the picture becomes more detailed. Dick and Norton still remain fairly stable, which makes them the strongest stylistic clusters in my Stylo results.

The most interesting case is H. G. Wells. *The Salvaging of Civilization* separates from many of the fiction texts. This makes sense because it is not really a narrative science fiction story in the same way as *The War of the Worlds* or *The Island of Doctor Moreau*. It is more essay-like and political. Stylo picks up that difference.

---

### Bootstrap Consensus Tree

![Stylo Bootstrap Consensus Tree](https://erazeerhead04.github.io/rlac/assets/images/stylo-consensus.png)

The consensus tree confirms that some author groups are more stable than others. Dick and Norton show strong grouping, while Brackett, Kuttner, and Zimmer Bradley are more mixed. This makes the corpus feel less like six completely separate author styles and more like a shared science fiction field with overlapping habits.

---

### Stylo PCA

![Stylo PCA 100 MFW](https://erazeerhead04.github.io/rlac/assets/images/stylo-pca-100.png)

![Stylo PCA 1000 MFW](https://erazeerhead04.github.io/rlac/assets/images/stylo-pca-1000.png)

The PCA images make the outliers easier to see. *The Salvaging of Civilization* is especially far away from the main group. *Jackie Sees a Star* also stands out. This suggests that even within one author’s work, style can vary depending on the type of story being told.

---

## TF-IDF: Looking for Content

TF-IDF works differently from Stylo. Instead of focusing on the most common words, it highlights words that are distinctive in one text compared with the rest of the corpus. Because of that, TF-IDF is better for looking at topic, theme, and content.

### TF-IDF PCA: 100 MFW

![TF-IDF PCA 100 MFW](https://erazeerhead04.github.io/rlac/assets/images/tfidf-100.png)

At 100 MFW, the texts are already spread out. Wells’s texts appear toward the right side, while Dick’s texts appear lower and more toward the left. *Jackie Sees a Star* is far away from many of the other texts, making it one of the clearest outliers.

---

### TF-IDF PCA: 300 MFW

![TF-IDF PCA 300 MFW](https://erazeerhead04.github.io/rlac/assets/images/tfidf-300.png)

At 300 MFW, the content groups become clearer. Norton’s texts appear closer together in the lower-right region. Dick’s texts also remain near each other. This suggests that TF-IDF is picking up shared vocabulary connected to each author’s recurring themes.

---

### TF-IDF PCA: 500 MFW

![TF-IDF PCA 500 MFW](https://erazeerhead04.github.io/rlac/assets/images/tfidf-500.png)

At 500 MFW, the pattern remains similar. Norton’s texts continue to group together, while Dick’s texts remain in their own region. Brackett and Zimmer Bradley sit closer to the middle, which makes sense because both often write stories connected to planets, strange worlds, and adventure.

---

### TF-IDF PCA: 2000 MFW

![TF-IDF PCA 2000 MFW](https://erazeerhead04.github.io/rlac/assets/images/tfidf-2000.png)

At 2000 MFW, the map becomes more stable. Wells’s texts remain strongly separated on the right. Norton’s texts remain lower and close together. Dick’s texts stay lower-left. This suggests that increasing the number of words strengthens the content-based patterns rather than removing them.

---

### TF-IDF PCA: 3000 MFW

![TF-IDF PCA 3000 MFW](https://erazeerhead04.github.io/rlac/assets/images/tfidf-3000.png)

At 3000 MFW, the same major pattern still holds. *The Salvaging of Civilization* stays far from the main fiction group. That tells me its vocabulary is not just slightly different. It is consistently different across many parameter settings.

---

## Comparing Stylo and TF-IDF

The most important difference between these methods is what they are good at showing.

Stylo groups texts by style. It helped me see that Dick and Norton have strong authorial signatures in this corpus. Their texts cluster together across multiple visualizations. Stylo also showed that Wells’s *The Salvaging of Civilization* is stylistically unusual because it is more like an essay than a story.

TF-IDF groups texts by content. It showed that Wells, Norton, and Dick occupy different thematic regions. Wells’s texts lean toward scientific, social, and philosophical vocabulary. Norton’s texts seem closer to adventure and planetary exploration. Dick’s texts are more connected to war, technology, machines, and instability.

The clearest example is *The Salvaging of Civilization*. Both methods treat it as an outlier, but for different reasons. Stylo sees it as stylistically different because it is not written like fiction. TF-IDF sees it as topically different because its vocabulary is more political and philosophical.

This shows that style and content are not completely separate. A political essay uses different words, but it also has a different rhythm and structure. Still, the two methods help us notice different parts of that difference.

---

## Reflection

Before doing this project, I expected the authors to cluster neatly. I thought each author would form a clear group. That happened with Dick and Norton, but not with everyone. At first, that seemed confusing. But now I think the messiness is actually useful.

Science fiction is a shared genre. These writers were working with overlapping ideas: space travel, strange planets, war, machines, alien societies, and future civilizations. So it makes sense that some authors overlap. The corpus does not only show individual style. It also shows shared genre pressure.

This connects to Ted Underwood’s warning about distant reading. A visualization can look very clear, but it does not explain itself. A cluster is not an argument by itself. It needs interpretation. We still have to ask why texts are close together, what words might be driving the result, and whether the pattern is about author, genre, theme, or form.

---

## Conclusion

This assignment showed me that computational reading works best when different methods are compared. Stylo and TF-IDF do not do the same thing. Stylo is better for studying style and authorship. TF-IDF is better for studying content and theme.

In my results, Dick and Norton were the strongest author clusters. Wells was the most interesting outlier, especially because *The Salvaging of Civilization* stood apart in both Stylo and TF-IDF. Brackett, Kuttner, and Zimmer Bradley were more mixed, which shows how much shared genre language matters in science fiction.

The main lesson is that distant reading does not replace close reading. It gives us patterns to investigate. The computer can show similarity and distance, but the human reader still has to explain what those patterns mean.

***Ready For Grading***
