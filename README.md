# Customer Segmentation & Psychographic Profiling

## Overview
This project applies Unsupervised Machine Learning to binary survey data to discover meaningful psychological profiles among respondents. By building a multi-engine clustering pipeline and applying range-based feature selection, abstract survey answers were translated into clear, actionable human personas.

## The Challenge
Standard clustering algorithms (like Scikit-Learn's default K-Means or Agglomerative Clustering with Euclidean distance) often fail or create highly imbalanced groups when applied to pure binary (Yes/No) survey data. This project required a custom approach to handle discrete data matrices and filter out "general population noise."

## Methodology & Tech Stack
* **Languages & Libraries:** Python, Pandas, Scikit-Learn, SciPy, Matplotlib, Gower.
* **The Pipeline:** Built a custom multi-engine experiment loop to evaluate combinations of distance metrics (Euclidean, Manhattan, Jaccard, Cosine) and linkages.
* **The Solution:** Implemented two successful tracks for handling the binary data:
  1. **Philosophy 1 (Transform the Data):** Dimensionality reduction via **PCA** followed by Euclidean distance and Ward linkage.
  2. **Philosophy 2 (Transform the Math):** Calculating a custom **Gower Distance** matrix using SciPy to properly evaluate categorical/binary dissimilarities, paired with Ward linkage.
* **Evaluation:** Used a custom "Range" filter to strip away questions everyone agreed on, isolating only the most polarizing traits to define the clusters.

## Key Findings: The 3 Personas
The model successfully grouped the audience into three highly distinct behavioral segments:

### 1. The Safe and Traditional (Cluster 0)
Defined by a strong preference for routine and stability. They are highly risk-averse, strictly obey rules and laws, and actively avoid unpleasant situations. They show almost zero desire to rebel or deviate from established societal norms.

### 2. The Happy Family People (Cluster 1)
Anchored by an overwhelmingly high rate of family harmony (97%), this segment is content, rule-abiding, and deeply satisfied with life. They believe their success comes from their own hard work, striking a balance between traditional values and an active, boredom-free lifestyle.

### 3. The Rebellious Explorers (Cluster 2)
Characterized by their thirst for novelty and independence, this group actively rejects traditional norms. They embrace risk, prioritize personal freedom ("I always do what I want"), and are constantly seeking to discover new things, often lacking the traditional family harmony seen in Cluster 1.