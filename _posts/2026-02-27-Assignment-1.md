---
title: "Assignment 1 - Institution, Identity, and Moral Legibility: Distant Reading Snape Across Canon and Fanfiction"
date: 2026-02-27
categories: [assignment-1, distant-reading, voyant, r]
tags: [HarryPotter, fanfiction, Voyant, tidytext, Snape]
---

## Introduction

Severus Snape is one of the Harry Potter series’ most contested moral figures: introduced as hostile and intimidating, later revealed as strategically ambiguous, and finally reframed through backstory and sacrifice. That moral arc matters because it is also an *information arc*: Rowling manages reader belief through partial access, delayed explanation, and repeated institutional cues (teacher/student hierarchy, punishment, surveillance, ministry control). Fanfiction frequently rewrites this management of belief. In fandom, Snape is often rehabilitated earlier, made emotionally explicit, or relocated into alternative family structures and social networks.

This project asks whether those shifts appear at the level of language and distribution. Across a mixed corpus of Rowling novels and Harry Potter fanfiction, I test two linked claims:

1. **Institutional framing claim:** Canon’s language foregrounds Hogwarts houses and institutional roles more consistently than fanfiction, where affiliation and belonging are more likely to be reorganized.
2. **Moral-legibility claim:** Snape’s “evil vs good” legibility is not stable across books; it changes in *when* and *with what words* Snape appears—especially near terms tied to darkness, fear, love, and Lily.

Rather than treating distant reading as a shortcut to interpretation, I use it as a diagnostic: it reveals where attention clusters and where narrative emphasis is structured, then I return to interpretation to explain what those patterns can and cannot mean.


## Corpus and Context

### Canon texts (Rowling)
- *Harry Potter and the Sorcerer’s Stone* (Rowling)
- *Harry Potter and the Order of the Phoenix* (Rowling)
- *Harry Potter and the Half-Blood Prince* (Rowling)
- *Harry Potter and the Deathly Hallows* (Rowling)

### Fanfiction texts
- **Adoptive Kaiju** (Gojirahkiin) — re-situates care and kinship by placing Harry into a different protective structure.
- **Wishmaster / Djinn** (Invaderdoom) — introduces non-canonical magical logics that reshape power and obligation.
- **Dragonheart Caravan** (Witchdragon) — heavily reorganizes family structure and belonging, while still retaining recognizable canon anchors (including Snape).

These fan works are not “anti-canon”; they are *transformational*: they keep recognizable names and institutions, but re-weight what matters (care, belonging, alternative authority, chosen family). That makes them useful for comparing how institutional and moral language travels.


## Method

### Voyant Tools (exploratory EDA)
I built a Voyant corpus using all selected texts together. I used multiple Voyant panels to avoid over-relying on a single visualization:

- **Trends** to compare relative frequency of major characters across documents.
- **Bubblelines** to observe *distribution* (where mentions cluster) rather than only totals.
- **Links** to visualize term co-occurrence networks (which words appear in proximity and with what connective structure).

I took screenshots of key views and treated each figure as an argument: each one supports a specific claim.

### R / posit.cloud (structured comparison)
Voyant is strong at rapid discovery, but it is weaker at explicit reproducibility (custom dictionaries, normalization choices, and transparent pipelines). In R, I replicate and extend the Voyant findings by:

- tokenizing each text
- removing stopwords
- normalizing counts (per 10,000 words)
- measuring **Snape’s local semantic neighborhood** (words appearing near “snape” within a defined window)
- comparing canon vs fandom on pre-defined lexical categories (institutional + moral lexicons)

This division of labor matters: Voyant helps find patterns worth testing; R helps test them with clearer assumptions and repeatable code.


## Findings Part 1: Houses as Institutional Grammar (Canon baseline vs transformation)

![Figure 1. Bubblelines—Hogwarts houses across Rowling texts](assets/images/Houses.png)

**Figure 1** uses Bubblelines to track the four Hogwarts houses. The most immediate pattern is **Gryffindor dominance**: “gryffindor” appears more frequently and more consistently across the Rowling books in this corpus than the other houses, which have visibly smaller and less frequent bubbles.

Interpretively, this is not just “Gryffindor is talked about most.” It suggests something stronger: **house affiliation functions as narrative infrastructure**. Houses are not merely labels; they are a stable grammar for conflict and belonging, especially early in the series where the school organizes identity into formal categories. Not to mention Harry was from Gryffindor house. In the series, Gryffindor functions as a kind of moral baseline. The house is narratively positioned as heroic and central, which reinforces its dominance in story focus. However, this framing also reveals institutional imbalance, other houses receive less narrative interiority.

So Gryffindor isn’t just a personality type — it’s also a storytelling structure. It signals to readers who is likely to act, who is likely to lead, and who is likely to be framed as morally legible.

At the same time, the *absence* is analytically useful. Ravenclaw and Hufflepuff appear comparatively muted. This supports a long-standing reading of Hogwarts as a structurally unequal institution: it recognizes four houses formally but distributes narrative attention unevenly.

![Figure 2. Bubblelines showing Hogwarts house frequency across Rowling canon texts and fanfiction works, with larger bubbles indicating higher frequency and clustered distribution suggesting narrative emphasis patterns](assets/images/mix_house.png)

The mixed corpus also reveals a noticeable shift in house emphasis within fanfiction. In Witchdragon’s *Dragonheart Caravan*, Slytherin emerges as the second most discussed house overall and, within the fanfiction texts specifically, becomes the most frequently referenced house. This contrasts with the Gryffindor dominance observed in Rowling’s canon and suggests a redistribution of narrative attention. Slytherin is traditionally associated with ambition, cunning, and strategic thinking, traits often positioned in opposition to Gryffindor’s emphasis on bravery and moral directness. This opposition forms a central structural tension in the series, where Gryffindor and Slytherin function as symbolic counterparts representing competing value systems.

This shift in emphasis is closely tied to the figure of Severus Snape, a Slytherin character whose moral ambiguity complicates the binary opposition between the two houses. While Gryffindor is narratively framed as heroic and morally transparent, Slytherin—and particularly Snape—embodies strategic ambiguity, secrecy, and institutional complexity. By foregrounding Slytherin more prominently, fanfiction often reinterprets the traditional Gryffindor–Slytherin divide, challenging the series’ moral hierarchy and exploring alternative perspectives on loyalty, authority, and ethical action.

**How this becomes a canon–fandom question:** fanfiction often repairs this imbalance by redistributing affiliation (e.g., expanding Ravenclaw/Hufflepuff interiority, or making Slytherin belonging more complex). In the R section, I operationalize this as a measurable test: do fandom texts increase relative frequency of under-attended houses, or do they decrease house-talk entirely in favor of other belonging vocabularies?


## Findings Part 2: Character Salience and Narrative Focus (Trends)

![Figure 3. Trends—major character terms across the Rowling corpus](assets/images/characters.png)

In **Figure 2**, “harry*” dominates across all documents, which is expected given focalization and protagonist-centered narration. But the more interesting pattern is **how the supporting characters shift**:

- **Dumbledore** shows a pronounced rise in later narrative weight (especially in *Half-Blood Prince* and *Deathly Hallows* in most reader memories), consistent with the series’ turn toward history, institutional backstory, and strategic knowledge.
- **Snape** rises compared to early canon, reflecting how his narrative function expands: from antagonist-teacher to ambiguous operative.
- **Voldemort** also changes in relative frequency: rather than a steady presence, he intensifies as the series becomes war-oriented rather than school-mystery oriented.

A key methodological point: Trends provides relative frequency, not moral evaluation. Increased “snape*” does not mean Snape becomes “good”; it means the text increasingly requires him as a narrative hinge. That distinction—*frequency is not valuation*—is central to the ethical caution Ted Underwood raises about distant reading: quantitative clarity can produce interpretive overconfidence if we forget what the metric actually measures.


## Findings Part 3: Networked Power—Harry, Dumbledore, Snape, Voldemort (Links)

![Figure 4. Links—co-occurrence network for Harry, Dumbledore, Snape, Voldemort, Malfoy](assets/images/links.png)

The **Links** panel visualizes co-occurrence structure: which terms tend to appear near each other, forming a network. In **Figure 3**, *harry* is the largest node and the densest connector, which fits protagonist focalization. But two features matter more than size:

1. **Institutional proximity:** “dumbledore” links strongly into the same network region as “harry” and “voldemort,” reflecting how the plot frames Dumbledore as the institutional mediator between student life and war.
2. **Snape’s structural position:** “snape” appears connected within the same cluster rather than isolated. This supports an interpretive claim: Snape’s narrative role is not peripheral; it is structurally integrated into the central power triangle (Harry–Dumbledore–Voldemort).

Also visible is a common limitation of co-occurrence networks: high-frequency connective verbs like “said” rise easily and can distort interpretive emphasis. This becomes a good place to practice Underwood’s warning: a network can look like a “map of meaning,” but it is still a map of *proximity* and *token frequency*, not intention, irony, or moral stance.

<iframe style='width: 531px; height: 373px;' src='https://voyant-tools.org/tool/Mandala/?query=harry&query=dark&query=snape&query=hermione&query=dumbledore&query=love&query=lily&query=evil&query=voldemort&corpus=fbbf3785ce34c3874a619cc8dd246630'></iframe>

## Qualitative Layer: Is Snape “Evil” or “Good”? (Bubblelines + context logic)

![Figure 4. Bubblelines visualization comparing frequency and distribution of snape across four moral-semantic terms: dark, love, fear, and lily.](assets/images/mix_snape.png)

To address the moral-legibility claim, I used Bubblelines to compare **snape*** with **dark***, **fear**, **love***, and **lily** across the Rowling books in this corpus.

Three patterns stand out:

1. **Snape is not evenly distributed across the series.** He becomes more prominent in later books, which is consistent with narrative reveal structure: as the series approaches its end, Rowling must “spend” withheld information and reposition readers’ beliefs.
2. **Love and Lily intensify late.** The *late clustering* of “lily” and higher visibility of “love*” near the later books is consistent with the series’ retroactive explanation strategy: Snape’s motivation becomes legible through a relational key (Lily) rather than through institutional role alone (professor/spymaster).
3. **Dark and fear persist across books, but do not settle the moral question.** “dark*” and “fear” appear broadly, which suggests they function as ambient genre vocabulary (war, threat, danger) rather than uniquely “Snape-coded” terms.

So, is Snape portrayed as evil or good? **The distant-reading answer is: neither—at least not directly.** What the data supports is a different claim:

> Snape’s moral status is managed through *timing and adjacency*: early books allow “Snape” to circulate without explanatory anchors; later books increase the density of relational anchors (“lily,” “love*”) that make a “good” interpretation narratively plausible.

This is exactly where distant reading must be paired with interpretive discipline. Frequency and distribution show the *architecture of emphasis*, not the moral truth-value of a character.

In the R section below, I make this more precise by measuring **words that occur near “snape”** (a local context window) and comparing whether that neighborhood is more strongly weighted toward threat vocabulary (e.g., dark, fear) or relational vocabulary (e.g., love, lily) across canon vs fandom.


## Why Fanfiction Matters Here

Fanfiction does not simply “liberate” characters from canon institutions; it often **rebuilds institutions in different forms**: chosen family, alternative mentorship, informal power structures, and transformed obligations. For example, *Dragonheart Caravan* retains Snape as “Professor Snape” but relocates him into an exchange relationship with a child character (letters, ingredients, mentorship), which reframes authority as *care plus expertise* rather than discipline alone. That relational reframing is visible directly in-text when Snape is addressed formally as “Professor Snape” within a negotiated, almost client-like exchange.

This reinforces the core comparative claim of the assignment: fandom is not absence of structure; it is **structural redistribution**.


### R Findings: Snape’s moral neighborhood in canon and fandom

R was used to formalize what Voyant suggested visually: that Snape’s moral “readability” is managed through patterns of adjacency rather than direct moral labeling. Instead of asking whether Snape is “good” or “evil” in an abstract sense, the R workflow tested a narrower linguistic question: **which moral or relational terms tend to appear in the same textual environments as “snape”?**

#### 1) Document-level association (pairwise correlations)

Across the corpus, the strongest document-level association for Snape is with **dark**:

- **snape ↔ dark**: correlation **0.888**
- **snape ↔ kill**: correlation **0.747**
- **snape ↔ cruel**: correlation **0.211**
- **snape ↔ fear**: correlation **0.121**
- **snape ↔ love**: correlation **0.0613**

The most surprising result is that **“evil” does not track with Snape**:

- **snape ↔ evil**: correlation **–0.0366** (slightly negative)

Similarly, the relational anchors that dominate late-series interpretation are not strongly aligned at the document level:

- **snape ↔ lily**: correlation **–0.198**
- **snape ↔ protect**: correlation **–0.201**
- **snape ↔ loyal**: correlation **–0.150**

**Interpretation.**  
At the scale of entire documents, Snape is statistically “closer” to the vocabulary of darkness and lethal stakes than to explicit moral labels (“evil”) or explicit virtue terms (“loyal,” “protect”). This supports a key literary point: **Rowling rarely needs to call Snape “evil” to make him *feel* morally suspect.** Suspicion is built through atmosphere terms (“dark”) and plot pressure terms (“kill”), which are widespread in late-series conflict.

Just as importantly, the weak/negative association with “lily” and “love” at the document level does *not* contradict your Voyant Bubblelines finding. It reveals a methodological fact: **document-level correlations are blunt instruments**. “Lily” can be extremely concentrated in one portion of one book (especially late), while remaining rare overall—making it crucial for interpretation but not dominant in whole-document statistics.

This is a direct example of Ted Underwood’s warning: the cleanest numeric signal is not always the most interpretively meaningful. A small lexical signal can still control a reader’s interpretation if it is placed strategically.

#### 2) Why I also computed a local context window

Because document-level correlation compresses entire books into a single vector, it can miss *where* meaning is produced. That is why the second R step builds a true token index and constructs a **±8-token window** around each occurrence of “snape.” This approach targets the question that matters most for moral legibility:

> When “snape” appears, what words tend to appear immediately near it?

This windowed method aligns better with the claims made from Voyant Bubblelines: Snape’s moral framing is not uniform across a whole novel; it is produced in local clusters (scenes, revelations, dialogue runs). The windowed results (summaries and plots) therefore provide a more faithful computational bridge between distant reading and interpretive reading.



## Reflection: what these methods reveal—and what they cannot

This project shows how distant reading helps reveal patterns of attention and narrative emphasis that are difficult to notice through close reading alone. Voyant and R make visible how institutional language, character frequency, and lexical distribution structure meaning across a large corpus. Rather than producing interpretation directly, these methods help identify where interpretation should focus.

At the same time, the analysis highlights the limits of quantitative approaches. As Underwood argues, frequency and correlation can appear authoritative but do not explain intention, context, or moral meaning. Patterns such as word proximity or character prominence indicate narrative emphasis, not ethical judgment. Distant reading therefore functions best as a diagnostic tool that complements interpretive reading rather than replacing it.


## Conclusion

This corpus-based comparison shows that canon and fanfiction differ not only in content but in how they structure institutional and moral meaning. In Rowling’s texts, house language functions as an organizing grammar: Gryffindor operates as a narrative and moral center, while other houses receive uneven attention. Character distribution reinforces this structure, with Harry as focal point, Dumbledore as institutional authority, and Voldemort as explicit antagonist. Snape occupies a transitional position between these roles, mediating secrecy, loyalty, and institutional conflict.

Fanfiction does not reject this structure but redistributes it. By foregrounding Slytherin and reconfiguring authority through alternative relationships and forms of belonging, works like *Dragonheart Caravan* challenge the canon’s implicit moral hierarchy and reframe institutional identity.

For Snape specifically, the evidence suggests that moral ambiguity is constructed through narrative staging rather than direct labeling. He aligns more strongly with atmospheric conflict vocabulary than with explicit moral terms, while relational explanations appear late and strategically. More broadly, the project shows how institutional language (houses), character salience, and lexical distribution interact to produce moral legibility. Distant reading does not resolve moral questions; it reveals the structural conditions under which those questions become meaningful.


<iframe style="width: 100%; height: 320px;" src="https://voyant-tools.org/tool/TextualArc/?corpus=fbbf3785ce34c3874a619cc8dd246630"></iframe>

## Works Cited

Underwood, Ted. *Distant Horizons: Digital Evidence and Literary Change*. University of Chicago Press, 2019. “The Risks of Distant Reading,” pp. 143–169.

“People Don’t Read, but LLMs Do.” Course reading.

Temple, Emily. “How Many Books Will You Read Before You Die?” Course reading.

Voyant Tools. https://voyant-tools.org/

R (tidytext / tidyverse) via posit.cloud notebooks.

**Ready For Grading**