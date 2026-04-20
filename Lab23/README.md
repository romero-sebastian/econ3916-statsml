# Lab CH23 — FedSpeak NLP Analysis

## P — Purpose
Convert 200+ FOMC meeting minutes (2000–2024) into quantitative sentiment
measures using TF-IDF and the Loughran-McDonald financial dictionary.
Cluster documents by linguistic similarity to detect Fed policy regimes.

## R — Role
Machine Learning student applying NLP text-as-data methods to central bank
communication. Tools: Python, HuggingFace datasets, scikit-learn, scipy.

## I — Instructions
1. Load FOMC Minutes from HuggingFace (`gtfintechlab/FOMC_Minutes`)
2. Preprocess and tokenize text
3. Build TF-IDF matrix (2000 features, bigrams)
4. Score each document with Loughran-McDonald sentiment dictionary
5. Visualize sentiment trends over time (2000–2024)
6. Cluster documents with K-Means on SVD-reduced TF-IDF vectors
7. Compare pre-2020 vs post-2020 sentiment with t-tests

## M — Methods
| Concept | Description |
|---|---|
| TF-IDF | Upweights rare, distinctive words per document |
| Loughran-McDonald | Financial domain sentiment dictionary |
| TruncatedSVD | Sparse matrix dimensionality reduction (like PCA) |
| K-Means | Clusters documents by linguistic similarity |
| t-test | Tests whether pre/post-COVID sentiment differs significantly |

## E — Evaluation
- TF-IDF captures regime-specific vocabulary (crisis vs. tightening vs. stable)
- LM sentiment reveals elevated negativity/uncertainty during GFC and COVID
- K-Means clusters align with known Fed policy regimes
- Post-2020 sentiment differs significantly from pre-2020 (p < 0.05)

## Dataset
- FOMC Minutes: `gtfintechlab/FOMC_Minutes` via HuggingFace
- 200+ documents, 2000–2024

## How to Run
1. Open `lab-ch23-guided.ipynb` in Google Colab or VS Code
2. Run cells top-to-bottom with Shift+Enter
3. All dependencies install in Cell 1

## Files
| File | Description |
|---|---|
| `lab-ch23-guided.ipynb` | Main notebook |
| `fomc_sentiment_time.png` | Sentiment time series 2000–2024 |
| `fomc_elbow.png` | Elbow + silhouette for cluster selection |
| `fomc_clusters.png` | PCA scatter of document clusters |
| `fomc_cluster_timeline.png` | Cluster assignments over time |
| `fomc_era_comparison.png` | Pre vs post-2020 boxplots |

## Author
Machine Learning — Lab Chapter 23
