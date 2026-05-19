# 🏀 NBA Player Archetype Discovery

> Unsupervised learning to discover data-driven NBA player archetypes — moving beyond the traditional 5-position system.

**MSBA · University of San Diego · Knauss School of Business**  
*Remi Robert · Enzo de Tomi · Nic Allen · Stephen Perrotta · Heath Salas*

---

## 📌 Overview

The traditional PG / SG / SF / PF / C classification system was designed decades ago and no longer reflects how modern NBA basketball is played. Players like Nikola Jokić (a "Center" who leads the league in assists) or Victor Wembanyama defy any single positional label.

This project applies **unsupervised machine learning** to the 2023–24 NBA season to discover statistically coherent player archetypes purely from performance data — no position labels used.

---

## 📊 Dataset

- **Source:** [NBA Stats (1947–Present)](https://www.kaggle.com/datasets/sumitrodatta/nba-aba-baa-stats) — Kaggle (Sumit Rodatta)
- **Scope:** 2023–24 regular season + multi-season analysis (4 seasons)
- **Filtering:** Minimum 10 mpg & 20 games played → **485 players**
- **Features (19):** Scoring, playmaking, rebounding, defense, advanced metrics (PER, BPM, VORP, TS%, Win Shares)

---

## 🔬 Methodology

| Step | Description |
|------|-------------|
| **Preprocessing** | StandardScaler normalization across all 19 features |
| **Optimal k** | Elbow Method + Silhouette Analysis (tested k = 2–12) |
| **Clustering** | K-Means (primary, n_init=20) |
| **Validation** | Hierarchical Clustering (Ward linkage) — ARI = 0.583 |
| **Visualization** | PCA reduction to 2D (PC1 + PC2 = 69.7% variance) |
| **Similarity** | KNN search for player comparisons |

---

## 🏷️ The Four Archetypes (k = 4)

| Cluster | Archetype | Size | Key Stats |
|---------|-----------|------|-----------|
| 0 | **Paint Big** | ~60 players | High ORB, BLK, TRB · Low 3P · Think Gobert, Capela |
| 1 | **Elite Star** | ~52 players | PTS +1.99 · AST +1.62 · PER +1.78 · VORP +2.10 · Think Jokić, LeBron, Curry |
| 2 | **Bench / Limited Role** | ~214 players | All metrics negative · Low minutes across the board |
| 3 | **Perimeter Wing / 3-and-D** | ~143 players | 3P +0.74 · STL +0.43 · Low BLK/REB |

---

## 📈 Key Findings

- **Positionless basketball is real** — Jokić, Giannis, and LeBron cluster together despite playing three different traditional positions
- **4 archetypes beat 5 positions** — k=4 yields the best meaningful silhouette score (0.250)
- **Strong PCA compression** — just 2 components capture 69.7% of all variance across 19 features
- **Methods agree** — ARI of 0.583 between K-Means and Hierarchical Clustering; strongest agreement on Elite Stars and Bench players
- **Archetypes are stable over time** — 79.8% average stay rate across 4 seasons confirms clusters capture real player types
- **Position labels are largely obsolete** — only Paint Big aligns with a traditional position (72% Centers); Elite Stars span all 5 positions

---

## 📂 Repository Structure

```
NBA-Clustering-Player-Value/
├── notebook.ipynb          # Full analysis: EDA, clustering, PCA, KNN
├── presentation.pdf        # Final project slides
└── README.md
```

---

## 🛠️ Tech Stack

`Python` · `scikit-learn` · `pandas` · `numpy` · `matplotlib` · `seaborn`

---

## 🔮 Next Steps

- Interactive player comparison dashboard
- Apply archetypes to lineup optimization and draft evaluation
- Explore DBSCAN for density-based clustering
