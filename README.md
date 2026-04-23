# SI699: Mental Health Topic Modeling & Risk Detection

This repository contains pipelines for analyzing mental health discussions on Reddit using topic modeling (BERTopic) and risk classification.

## Project Structure

```
├── data_processing.ipynb          # Data cleaning and preprocessing
├── topic_modeling_colab.ipynb     # BERTopic topic modeling pipeline
├── data/                          # Data files (tracked via Git LFS)
│   ├── reddit_mental_health_posts.csv
│   ├── processed_corpus.csv
│   ├── corpus_with_topics.csv
│   └── ...
├── outputs/
│   ├── figures/                   # Generated visualizations
│   ├── models/                    # Trained models
│   └── results/                   # Evaluation metrics and results
└── README.md
```

## Requirements

```bash
pip install bertopic sentence-transformers umap-learn hdbscan transformers torch
pip install datasets huggingface_hub scikit-learn pandas matplotlib seaborn gensim joblib
```

## How to Run

### 1. Data Processing

Run `data_processing.ipynb` to:
- Load Reddit mental health corpus from Hugging Face
- Clean text (remove URLs, HTML, whitespace)
- Filter deleted/removed and short posts
- Generate stratified sample for annotation
- Apply rule-based pre-annotation (Zirikly-style)

```python
# Output files:
# - data/processed_corpus.csv (87,733 cleaned posts)
# - data/sample_for_annotation.csv (1,200 posts for labeling)
# - data/annotated_subset.csv (with risk_level 0-3)
```

### 2. Topic Modeling

Run `topic_modeling_colab.ipynb` (designed for Google Colab) to:
- Compute MentalBERT embeddings
- Run BERTopic clustering
- Generate topic visualizations
- Evaluate model coherence and stability

**For Google Colab:**
1. Upload notebook to Colab
2. Mount Google Drive
3. Modify `DRIVE_BASE` path in Configuration cell
4. Run all cells

**Configuration:**
```python
# Modify these paths for your environment
DRIVE_BASE = Path("/content/drive/MyDrive/your_folder")
```

```python
# Output files:
# - data/corpus_with_topics.csv
# - outputs/results/bertopic_topic_info.csv
# - outputs/results/topic_modeling_metrics.csv
# - outputs/figures/*.png
```

## Key Results

- **Documents:** 87,733 Reddit posts from 5 subreddits (ADHD, Aspergers, Depression, OCD, PTSD)
- **Topics:** 21 coherent topics discovered
- **Coherence:** Cᵥ = 0.54 (acceptable for social media text)
- **Time Range:** July 2019 – December 2021

## Data Source

Reddit Mental Health Posts dataset from Hugging Face:
```python
from datasets import load_dataset
dataset = load_dataset('solomonk/reddit_mental_health_posts')
```

## Git LFS

Large files (CSV, model weights) are tracked via Git LFS:
```bash
git lfs install
git lfs pull
```

## License

For academic use only.
