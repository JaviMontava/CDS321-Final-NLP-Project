# Multilingual NLP Analysis of UEFA Euro 2024 Match Reports

**Author:** Javi Montava  
**University:** George Mason University  
**Course:** CDS 321 — Natural Language Processing  
**Semester:** Fall 2026

## 1. Project Overview

This project investigates multilingual natural language processing techniques applied to UEFA Euro 2024 football journalism.

The analysis combines multilingual sentiment analysis, football-specific vocabulary analysis, semantic similarity, cross-lingual document retrieval, and player-information ablation.

The main objective is to evaluate whether multilingual NLP representations can identify semantic correspondence between football reports written in different languages.

## 2. Dataset

The original dataset is obtained from the publicly accessible SocCor corpus:

https://github.com/PaulLoehr/SocCor

The corrected research dataset contains:

| Characteristic | Value |
|---|---:|
| Articles | 153 |
| Football matches | 51 |
| News sources | 3 |
| Languages | 3 |
| Dataset columns | 18 |

The three news sources are:

- BBC — English
- Marca — Spanish
- Kicker — German

Each match is represented by one article from each source.

The original article corpus is downloaded directly from SocCor rather than redistributed in this repository.

## 3. Dataset Corrections

A manual article-alignment audit identified three swapped pairs of article assignments:

- Marca: Matches 17 and 18
- BBC: Matches 49 and 50
- Marca: Matches 49 and 50

These corrections are implemented automatically in the notebook.

The original document ordering is restored using the published dataset_row_order.csv file.

The reconstructed dataset is validated using an exact SHA256 fingerprint across eight columns and all 153 documents.

Expected SHA256:

```text
f7199d50f29d2177c0827cd0dda18e42b0218b8e6a610cf5c397c1709fd402f9
```

## 4. Repository Structure

```text
CDS321-Final-NLP-Project/
│
├── README.md
├── requirements.txt
├── CDS321_Single_Final_Notebook_JaviMontava.ipynb
│
├── data/
│   └── dataset_row_order.csv
│
└── results/
    ├── euro2024_sentiment_results_corrected_v2.csv
    ├── euro2024_football_vocabulary.csv
    ├── euro2024_tfidf_improved.csv
    ├── euro2024_document_embeddings_corrected_v2.npy
    ├── euro2024_ablation_embeddings_corrected_v2.npy
    ├── euro2024_embedding_metadata_corrected_v2.csv
    └── euro2024_ablation_metadata_corrected_v2.csv
```

## 5. How to Run the Project

Google Colab is the recommended execution environment.

### Step 1 — Open the notebook

Open CDS321_Single_Final_Notebook_JaviMontava.ipynb in Google Colab.

Alternatively, download the notebook from this repository and upload it to Google Colab.

### Step 2 — Select the default execution mode

Keep the following setting:

```python
RUN_UPSTREAM = False
```

### Step 3 — Execute the notebook

Select:

Runtime → Run all

The notebook automatically:

1. Clones the public project repository.
2. Downloads the original SocCor articles and match metadata.
3. Reconstructs the corrected dataset.
4. Applies the original NLP preprocessing.
5. Restores the validated document ordering.
6. Verifies dataset integrity using SHA256.
7. Loads the validated cached NLP outputs.
8. Recomputes statistical analyses and retrieval metrics.
9. Generates the final research visualizations.

No personal Google Drive access, authentication, or manual dataset uploads are required.

### Step 4 — Verify dataset integrity

The dataset validation should report:

```text
Validated documents: 153
Validated columns: 8
Exact match: True
Google Drive required: NO
VALIDATION: PASSED
```

## 6. NLP Methodology

The project includes:

- Multilingual sentiment classification using XLM-RoBERTa.
- Football-specific multilingual vocabulary analysis.
- TF-IDF analysis.
- Multilingual sentence-transformer document embeddings.
- Cosine similarity analysis.
- Cross-lingual document retrieval.
- Player-information ablation.
- Statistical hypothesis testing.
- Match-cluster bootstrap uncertainty estimation.

The principal transformer models are:

- cardiffnlp/twitter-xlm-roberta-base-sentiment
- sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2

## 7. Main Results

### Semantic Similarity

| Metric | Result |
|---|---:|
| Same-match cosine similarity | 0.8552 |
| Different-match cosine similarity | 0.7261 |
| Difference | 0.1291 |

### Cross-Lingual Retrieval

| Metric | Original | Player-masked |
|---|---:|---:|
| Recall@1 | 74.18% | 60.13% |
| Recall@5 | 95.75% | 83.01% |
| Mean Reciprocal Rank | 0.8296 | 0.7094 |

Removing identifiable player information reduces Recall@1 by approximately 14.05 percentage points.

The results suggest that player information contributes meaningfully to cross-lingual match retrieval.

## 8. Generated Visualizations

The notebook generates four principal research figures:

- FINAL_01_sentiment.png
- FINAL_02_vocabulary.png
- FINAL_03_semantic_similarity.png
- FINAL_04_retrieval_ablation.png

These figures are saved in the local results directory.

## 9. Reproducibility Scope

The default execution mode reconstructs the original corrected dataset and uses validated cached NLP outputs to reproduce the final statistical analyses, retrieval metrics, ablation comparisons, and visualizations.

An optional upstream model regeneration pipeline is included in the notebook and can be enabled using:

```python
RUN_UPSTREAM = True
```

This optional mode requires additional computational resources and transformer dependencies.

Regenerated outputs are stored separately and do not replace the validated cached research artifacts used by the downstream analyses.

The optional upstream pipeline has not been independently validated as a complete end-to-end execution.

## 10. Limitations

- News source and language are confounded.
- The dataset covers a single football tournament.
- The sentiment model was primarily trained on social-media text.
- Multilingual vocabulary dictionaries were not independently validated for equivalent coverage.
- Semantic results depend on the selected embedding model.
- Retrieval queries associated with the same matches are statistically dependent.
- AI-assisted sentiment annotations are not independent human ground truth.

The results should therefore be interpreted as observational rather than causal evidence.

## 11. Data Attribution

The original multilingual football corpus is provided by the SocCor project:

https://github.com/PaulLoehr/SocCor

This repository provides the student's research implementation, experimental analyses, derived NLP artifacts, dataset alignment information, and reproducibility documentation.

The original article corpus remains available through its original source.

## 12. Academic Submission

This repository accompanies the final project submitted for CDS 321 — Natural Language Processing at George Mason University.

The final Jupyter notebook contains the implementation, methodological documentation, statistical analyses, visualizations, results, and conclusions.
