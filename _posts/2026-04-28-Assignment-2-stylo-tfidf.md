---
layout: post
title: "Style vs Content: Comparing Stylo and TF-IDF in a Science Fiction Corpus"
date: 2026-04-28
---

## Introduction

This project explores how two computational methods—Stylo and TF-IDF—interpret a shared corpus of eighteen science fiction texts from Project Gutenberg. While both methods aim to identify similarity between texts, they operate very differently. Stylo focuses on the most frequent words and is often used to detect authorial style. TF-IDF, on the other hand, emphasizes distinctive vocabulary and is better suited to identifying themes and content.

Working through both methods, I found that they do not contradict each other, but instead reveal different layers of the same corpus. Stylo tends to group texts by how they are written, while TF-IDF groups them by what they are about.

---

## Stylometry (Stylo): Patterns of Writing Style

The first method I used was Stylo, which analyzes patterns in the most frequent words. These words are often function words such as “the,” “and,” and “of,” which tend to reflect unconscious stylistic habits.

### Cluster Analysis (100 MFW)

![Stylo Cluster 100 MFW](/assets/images/assignment2/stylo-100mfw.png)

At 100 MFW, the clustering already shows strong author signals. Philip K. Dick’s texts cluster tightly together, suggesting a consistent writing style. Andre Norton’s texts also form a clear group. This indicates that Stylo is effectively capturing stylistic consistency.

However, not all authors behave the same way. Brackett and Kuttner texts appear more mixed, suggesting shared stylistic conventions—likely due to their connection to pulp science fiction traditions.

---

### Cluster Analysis (500 MFW)

![Stylo Cluster 500 MFW](/assets/images/assignment2/stylo-500mfw.png)

At 500 MFW, the clustering becomes slightly more refined but also more complex. Dick and Norton remain stable, while Brackett, Kuttner, and Zimmer Bradley show more overlap.

One important observation is that H. G. Wells’s *The Salvaging of Civilization* sits far from the rest. This reflects its non-fiction, essay-like style, which differs significantly from narrative science fiction.

---

### Bootstrap Consensus Tree

![Stylo Consensus Tree](/assets/images/assignment2/stylo-consensus.png)

The consensus tree reinforces these patterns. It shows that while some authors cluster reliably, the corpus as a whole shares stylistic similarities. This suggests that genre conventions—especially mid-century science fiction—play a role alongside individual author style.

---

### PCA (Stylo)

![Stylo PCA 100](/assets/images/assignment2/stylo-pca-100.png)

![Stylo PCA 1000](/assets/images/assignment2/stylo-pca-1000.png)

The PCA visualizations highlight outliers more clearly. *The Salvaging of Civilization* is consistently far removed, confirming its stylistic difference. *Jackie Sees a Star* is also unusually distant, suggesting variation within Zimmer Bradley’s own writing.

---

## TF-IDF: Patterns of Content and Theme

Unlike Stylo, TF-IDF emphasizes words that are distinctive within each text. This makes it more sensitive to topic and theme rather than style.

---

### TF-IDF PCA (100 MFW)

![TF-IDF 100](/assets/images/assignment2/tfidf-100.png)

At 100 MFW, the texts are widely spread out. Even at this level, clear thematic separations emerge. Wells’s texts tend toward the right, while Dick’s texts appear lower and to the left.

---

### TF-IDF PCA (300 & 500 MFW)

![TF-IDF 300](/assets/images/assignment2/tfidf-300.png)

![TF-IDF 500](/assets/images/assignment2/tfidf-500.png)

As the number of words increases, clusters become clearer. Norton’s texts group in the lower-right region, reflecting shared vocabulary related to space travel and planetary exploration. Dick’s texts remain grouped in a different region, likely reflecting themes of war, machines, and instability.

---

### TF-IDF PCA (2000 & 3000 MFW)

![TF-IDF 2000](/assets/images/assignment2/tfidf-2000.png)

![TF-IDF 3000](/assets/images/assignment2/tfidf-3000.png)

At higher MFW levels, the clustering stabilizes. Wells’s texts remain strongly separated on the right, especially *The Salvaging of Civilization*, which consistently appears as an extreme outlier. This reflects its distinct vocabulary, which is more philosophical and political than narrative.

---

## Comparison: Style vs Content

The most important takeaway from this project is that Stylo and TF-IDF reveal different kinds of similarity.

Stylo groups texts by **style**. It shows that Dick and Norton have strong and consistent authorial signatures. It also shows how genre can blur stylistic boundaries, especially for authors like Brackett and Kuttner.

TF-IDF groups texts by **content**. It highlights thematic regions within the corpus: Wells’s philosophical writing, Norton’s adventure narratives, and Dick’s technological and war-focused stories.

One clear example of disagreement is Wells’s *The Salvaging of Civilization*. In Stylo, it is an outlier because of its essay-like style. In TF-IDF, it is also an outlier, but for a different reason—its vocabulary reflects political and social analysis rather than fiction.

This demonstrates that style and content are not completely separable, but they can still be analyzed independently.

---

## Conclusion

Working with both Stylo and TF-IDF made it clear that computational analysis does not produce a single “correct” interpretation. Instead, it offers multiple perspectives on the same corpus.

Stylo reveals how authors write. TF-IDF reveals what they write about.

Together, they provide a more complete understanding of the texts than either method alone. At the same time, the results remind us that interpretation still matters. Clusters and plots do not explain themselves—they need to be read, questioned, and connected back to the texts.

This project ultimately shows that distant reading is not about replacing close reading, but about expanding it.