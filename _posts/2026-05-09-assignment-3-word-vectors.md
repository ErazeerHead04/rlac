---
title: "Assignment 3 - Machines, Minds, and Planets: Exploring Word Vector Models in a Science Fiction Corpus"
date: 2026-05-09
categories: [Assignment-3]
tags: [ScienceFiction, ProjectGutenberg, Word2Vec, WordVectors, DistantReading, PositCloud]
---

## Introduction

Science fiction often builds meaning through repeated relationships among ships, planets, machines, aliens, bodies, and minds. These words are familiar genre markers, but they do not mean the same thing in every context. A “ship” can belong to older sea-adventure language, or it can become a spaceship. A “machine” can be a practical tool, a technological environment, or a source of anxiety. A “mind” can refer to ordinary thought, scientific consciousness, alien intelligence, or psychological experience.

For this assignment, I use pretrained word2vec models to explore how a Project Gutenberg science fiction corpus represents three connected areas of meaning: **space exploration**, **machine technology**, and **human experience**. My main research question is:

> How do different word-vector models represent the relationship between space, technology, and human experience in a public-domain science fiction corpus?

My argument is that the models represent science fiction through three related semantic fields: planets and space as places of travel and settlement, machines as both practical mechanisms and genre technologies, and the mind as a more abstract field of thought and perception. Smaller-window models often show more immediate associations, while larger-window and higher-dimensional models make broader thematic relationships more visible. However, these vector results are not interpretations by themselves. They become meaningful only when they are connected to corpus knowledge, model parameters, and careful human interpretation.

---

## Corpus and Method

The corpus for this assignment contains about 1000 science fiction texts from Project Gutenberg. Because these texts come from the public domain, the corpus likely represents older science fiction more strongly than recent science fiction. That matters because the model may learn relationships shaped by older adventure fiction, early scientific romance, exploration narratives, and older technological vocabulary. I therefore treat these results as evidence about this particular corpus, not as universal claims about all science fiction.

I used pretrained word2vec models in the Posit Cloud notebook rather than training new models. Word2vec does not learn meaning through dictionary definitions. It learns from context: if two words tend to appear near similar surrounding words, the model places them near each other in vector space. This makes word vectors useful for exploratory literary analysis because genre is partly made from repeated contexts. But this also creates a limitation: the model can show patterns of similarity, but it cannot explain tone, irony, plot, or historical meaning by itself.

I compared four models:

| Model | Dimensions | Window | Why I used it |
|---|---:|---:|---|
| `model_100d_w4` | 100 | 4 | Tight local context |
| `model_100d_w6` | 100 | 6 | Balanced baseline |
| `model_200d_w10` | 200 | 10 | Broader thematic context |
| `model_300d_w8` | 300 | 8 | Richer and more complex associations |

I selected four models rather than all six because I wanted the comparison to remain readable. The models allow me to compare local context against broader thematic context, and lower-dimensional representations against richer ones. Window size matters because it controls how much surrounding text counts as context. Dimensionality matters because it changes how much complexity the model can represent. I do not treat the larger model as automatically better; I treat each model as a different lens.

The main methods I used were nearest-neighbor search, clustering, and one analogy experiment. Nearest-neighbor search shows which words are closest to a target word. Clustering groups selected words based on vector similarity. The analogy experiment uses vector arithmetic to test a semantic transformation.

---

## Space and Exploration: “ship”

I began with the word **ship** because it is one of the most important words for science fiction. It can connect older travel and naval adventure to futuristic space travel.

![Figure 1. Closest words to "ship" across four word-vector models](https://erazeerhead04.github.io/rlac/assets/images/ship_similarity_graph.png)

**Figure 1.** Closest words to “ship” across four word-vector models. The graph shows that “ship” is associated with both older travel vocabulary and science-fiction transportation vocabulary.

| Model | Closest words | Interpretation |
|---|---|---|
| `model_100d_w4` | spacer, flagship, submarine, Serpent, beam, asteroid, Valiant, city | Mix of space, naval, and named-vessel language |
| `model_100d_w6` | spacer, flagship, asteroid, submarine, beam, Nemesis, barrage, city | Balanced mix of space and conflict vocabulary |
| `model_200d_w10` | spacer, asteroid, flagship, globe, submarine, spaceships, barrage, beam | Broader thematic link between travel and space |
| `model_300d_w8` | spacer, flagship, asteroid, spaceships, beam, globe, submarine, Nemesis | Richer but still stable space-travel pattern |

The nearest words to “ship” show that the model connects ship vocabulary to both older travel language and science-fiction space language. Words such as “submarine” and “flagship” suggest older naval or adventure contexts, while words such as “spacer,” “asteroid,” “beam,” and “spaceships” move the word into a science-fiction setting. This is useful because it shows that “ship” is not only a spaceship term in the corpus. It carries older exploration meanings into futuristic settings.

The models are also fairly stable. “Spacer,” “flagship,” “submarine,” “asteroid,” and “beam” appear across multiple models. This stability suggests that the word has a strong semantic neighborhood in the corpus. At the same time, the appearance of words such as “Serpent,” “Valiant,” and “Nemesis” reminds me that word-vector models can also capture proper names or specific textual contexts. This is a good reminder not to treat every result as a general genre pattern.

---

## Space and Place: “planet”

The word **planet** gives a related but slightly different view of science fiction space. While “ship” emphasizes movement, “planet” emphasizes location, settlement, and world-building.

| Model | Closest words | Interpretation |
|---|---|---|
| `model_100d_w4` | land, Mars, Pluto, ship, asteroid, Titan, country, city | Planet as both astronomical object and place |
| `model_100d_w6` | Mars, land, Pluto, asteroid, ship, universe, Titan, city | Strong astronomical and travel associations |
| `model_200d_w10` | Mars, Pluto, asteroid, land, ship, Titan, universe, planetary | More explicit space and planetary vocabulary |
| `model_300d_w8` | Mars, land, ship, asteroid, universe, planetary, city, country | Space mixed with settlement and social place |

The nearest words to “planet” show that the model treats planets as both astronomical objects and possible inhabited worlds. Words such as “Mars,” “Pluto,” “asteroid,” “Titan,” “universe,” and “planetary” belong clearly to space vocabulary. But words such as “land,” “country,” and “city” suggest that planets also function like social and geographical spaces. They are not only objects in space; they are places that can be entered, mapped, inhabited, and contested.

This result supports one of the central patterns in science fiction: outer space is often imagined through familiar forms of place. A planet becomes a world, a country, a city, or a landscape. The model does not explain that historical transformation by itself, but it helps make the pattern visible.

---

## Machines and Technology: “machine”

The word **machine** is useful because it tests whether the model represents technology as a practical object, a science-fiction device, or something more socially and thematically charged.

![Figure 2. Closest words to "machine" across four word-vector models](https://erazeerhead04.github.io/rlac/assets/images/machine_similarity_graph.png)

**Figure 2.** Closest words to “machine” across four word-vector models. The graph highlights how machine vocabulary connects to mechanisms, instruments, engines, and science-fiction technologies.

| Model | Closest words | Interpretation |
|---|---|---|
| `model_100d_w4` | mechanism, machinery, unit, ship, televisor, instrument, model, engines | Technical and mechanical context |
| `model_100d_w6` | mechanism, machinery, unit, ship, clockwork, instrument, engines, model | Stable mechanical vocabulary |
| `model_200d_w10` | mechanism, unit, machinery, model, cogs, keyboard, balloon, clockwork | Broader machine and device context |
| `model_300d_w8` | mechanism, machinery, ship, balloon, unit, keyboard, instrument, automatic | Richer but more mixed technology field |

The results for “machine” are strongly technical. Words such as “mechanism,” “machinery,” “instrument,” “engines,” “cogs,” “clockwork,” and “automatic” suggest that the model understands machine vocabulary through physical and mechanical contexts. However, the appearance of words such as “ship,” “televisor,” “keyboard,” and “balloon” also connects machinery to science-fiction world-building. Technology is not just background equipment in this corpus. It is part of the imagined environment.

The “machine” results are also interesting because they do not only point to advanced futuristic technology. “Clockwork,” “cogs,” and “mechanism” feel older or more mechanical than digital. This makes sense for a public-domain corpus, where much of the technological imagination may come from earlier industrial and mechanical contexts rather than contemporary computing. In this case, the corpus history matters for interpretation.

---

## Human Experience: “mind”

The word **mind** is more abstract than “ship,” “planet,” or “machine.” I used it to test whether the model could capture vocabulary connected to thought, perception, and human interiority.

| Model | Closest words | Interpretation |
|---|---|---|
| `model_100d_w4` | brain, thoughts, conscience, spirit, Lens, memories, dream, mood | Thought and inner experience |
| `model_100d_w6` | brain, thoughts, conscience, spirit, memories, belief, sensations, ideas | Mental and emotional vocabulary |
| `model_200d_w10` | brain, thoughts, conscience, intellect, mood, memories, sensations, perception | More abstract cognitive vocabulary |
| `model_300d_w8` | brain, thoughts, conscience, memories, intellect, ideas, sensations, spirit | Stable consciousness and perception pattern |

The results for “mind” are more abstract than the results for “ship,” “planet,” or “machine.” Words such as “brain,” “thoughts,” “conscience,” “spirit,” “memories,” “sensations,” “ideas,” and “perception” suggest that the model connects mind to thought, feeling, memory, and consciousness. This is useful because it shows that the corpus is not only about objects and places. It also includes interior experience.

At the same time, “mind” is harder to interpret because abstract terms can appear in many different kinds of contexts. A word like “ship” has a more concrete semantic field, while “mind” can belong to philosophy, psychology, alien intelligence, memory, or emotion. The model captures this broadness, but it does not tell me which kind of scene produced the association. This is one place where close reading or AntConc concordance searching would be useful as a follow-up.

---

## Clustering Selected Science Fiction Vocabulary

After looking at individual target words, I tested a smaller selected list of science-fiction vocabulary using clustering. I used words connected to space, machines, and human experience.

| Cluster | Words | Interpretation |
|---|---|---|
| Cluster 1 | mind, man, woman, people, war, time | Human and social experience |
| Cluster 2 | planet, star, earth, space, alien, city, world | Space, place, and world-building |
| Cluster 3 | ship, crew, machine, robot, engine, metal, body | Technology, travel, and machinery |

The clustering result mostly separates the vocabulary into three meaningful groups. Cluster 2 clearly gathers space and world-building words such as “planet,” “star,” “earth,” “space,” “alien,” “city,” and “world.” Cluster 3 connects “ship,” “crew,” “machine,” “robot,” “engine,” “metal,” and “body,” which is especially interesting because it joins transportation, machinery, and embodiment. This suggests that in this model, technology is not separate from human bodies or travel. Cluster 1 gathers “mind,” “man,” “woman,” “people,” “war,” and “time,” which points toward human and social experience.

The clusters are not perfect categories, but that is part of the finding. The model does not organize words according to my categories. It organizes them according to repeated contexts in the corpus.

![Figure 3. Word2Vec PCA overview](https://erazeerhead04.github.io/rlac/assets/images/visualization.png)

**Figure 3.** Word2Vec PCA overview. I include this figure mainly as a methodological caution: when too many words are plotted at once, the visualization becomes dense and difficult to interpret. For that reason, the targeted tables and selected-word clustering are more useful for my argument than a large all-vocabulary map.

The PCA visualization is useful as a reminder that visualizations do not automatically clarify interpretation. A graph can look scientific while still being too crowded to support a focused claim. This connects directly to a broader lesson from the course: computational evidence needs explanation. The clearest-looking visualization is not always the most meaningful one.

---

## Analogy: `ship - sea + space`

The final experiment used vector arithmetic. I tested the analogy:

> **ship - sea + space**

In plain language, this asks what happens if the model removes a sea-travel context from “ship” and adds a space context.

| Rank | Result word |
|---:|---|
| 1 | ship |
| 2 | space |
| 3 | spaceship |
| 4 | speedster |
| 5 | hyperspace |
| 6 | warp |
| 7 | flitter |
| 8 | rocket |
| 9 | shuttle |
| 10 | freighter |

The analogy result was one of the clearest pieces of evidence in the analysis. The model returned words such as “spaceship,” “hyperspace,” “warp,” “rocket,” “shuttle,” and “freighter.” This suggests that when the model removes a sea-travel context from “ship” and adds a space context, the word moves strongly toward science-fiction transportation.

This result is useful because it shows how science fiction transforms older exploration vocabulary into futuristic travel vocabulary. A ship is not only replaced by a spaceship; rather, the older idea of travel is carried into a new technological and cosmic setting. Still, I would not treat the analogy as proof. Vector arithmetic is suggestive, but literary meaning is rarely as clean as a mathematical equation. The analogy works best as a way to generate an interpretive question: how does science fiction inherit older travel language and redirect it toward space?

---

## Reflection and Limitations

These results are useful, but they also show the limits of word-vector analysis. A nearest-neighbor table can look very persuasive, but it does not explain the passages that produced the relationship. The model can show that words appear in similar contexts, but it cannot explain tone, plot, character perspective, or historical meaning by itself. Human interpretation is still necessary.

This connects to Ted Underwood’s warning that the cleanest numeric signal is not always the most interpretively meaningful one. In this assignment, the strongest results were not simply the neatest lists of words. The strongest results were the ones that helped me ask better questions about the corpus: why does “ship” move between sea and space? Why does “body” cluster with machines? Why does “mind” produce more abstract and unstable associations?

There are also corpus limitations. Since the corpus comes from Project Gutenberg, it is shaped by public-domain availability. It likely overrepresents older science fiction and underrepresents more recent science fiction, especially works still under copyright. That affects what the model can learn. For example, the strong mechanical vocabulary around “machine” may reflect older technological imagination more than contemporary digital culture.

Finally, model parameters matter. A smaller window may capture more immediate word relationships, while a larger window may capture broader thematic relationships. Higher dimensions can capture more nuance, but that does not automatically make interpretation better. More complex models can produce richer associations, but they can also make results harder to explain. For literary analysis, the best model is not always the largest one; it is the one whose results can be interpreted responsibly.

---

## Conclusion

Overall, word vectors helped me see science fiction as a genre built from repeated relationships among exploration, technology, and human experience. The models were especially strong at identifying concrete genre vocabulary around ships, planets, machines, and space travel. They were less straightforward with abstract concepts like mind and perception.

The “ship” results showed how older exploration vocabulary carries into science-fiction travel. The “planet” results showed that outer space becomes a place of settlement, geography, and world-building. The “machine” results showed a technological imagination shaped by mechanisms, instruments, engines, and devices. The “mind” results showed that the corpus also contains vocabulary of thought, memory, and consciousness, although this field is more abstract and harder to interpret.

For that reason, I would describe word2vec not as a replacement for reading, but as a tool for finding patterns that deserve closer reading. It can show where words gather, but the human reader still has to explain why those gatherings matter.

## Works Cited

Underwood, Ted. *Distant Horizons: Digital Evidence and Literary Change*. University of Chicago Press, 2019.

Project Gutenberg Science Fiction Corpus. Course corpus.

R / Posit Cloud Word Vectors notebook.

word2vec R package.

***READY FOR GRADING***
