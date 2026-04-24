# Topic Modeling on Reddit Mental Health Posts

This part of the project involves data preprocessing, topic modeling using BERTopic with MentalBERT embeddings, quantitative evaluation (coherence, stability), and temporal analysis of mental health discussions on Reddit.

## Data Source

Primary corpus comes from a publicly available dataset on Hugging Face, which contains approximately 151,000 Reddit posts from five mental health subreddits: depression, PTSD, OCD, ADHD, and Aspergers.

## Project Structure

```text
├── data/                                               Data files (tracked via Git LFS)
│   ├── reddit_mental_health_posts.csv                  Raw data from Hugging Face
│   ├── processed_corpus.csv                            Cleaned corpus (87,733 posts)
│   ├── corpus_with_topics.csv                          Corpus with topic assignments
│   ├── labeled_with_topics.csv                         Labeled data with topics
│   ├── sample_for_annotation.csv                       Stratified sample for annotation
│   └── annotated_subset.csv                            Rule-based pre-annotated data
│
├── outputs/
│   ├── figures/                                        Generated visualizations
│   │   ├── topic_distribution.png
│   │   ├── topic_prevalence_over_time.png
│   │   ├── topic_similarity.png
│   │   ├── topic_trends.png
│   │   ├── topic_words_heatmap.png
│   │   └── topics_per_subreddit.png
│   │
│   ├── models/                                         Trained models
│   │   ├── roberta_risk_model/
│   │   └── sbert_risk_model/
│   │
│   └── results/                                        Evaluation metrics and results
│       ├── bertopic_topic_info.csv
│       ├── topic_modeling_metrics.csv
│       ├── topic_prevalence_over_time.csv
│       ├── topic_stability_results.csv
│       └── topics_for_integration.csv
│
├── .gitattributes
├── .gitignore
├── data_processing.ipynb                               Data cleaning and preprocessing
├── topic_modeling_colab.ipynb                          BERTopic topic modeling pipeline
├── README.md
└── requirements.txt
```

## Running Code

1. Download the data from this repository by either using `git clone https://github.com/Social-Media-Help-Seeking-ML/yinjasim.git` for HTTPS or using `git clone git@github.com:Social-Media-Help-Seeking-ML/yinjasim.git` for SSH. It can also be downloaded manually by clicking on **Code >> Download Zip**.

2. Install Git LFS and pull large files:
   ```bash
   git lfs install
   git lfs pull
   ```

3. Create a virtual environment and activate it.

4. Install necessary packages listed on the `requirements.txt` into the virtual environment:
   ```bash
   pip install -r requirements.txt
   ```

5. Run `data_processing.ipynb` for data loading, cleaning, filtering, and stratified sampling for annotation.

6. Run `topic_modeling_colab.ipynb` for topic modeling pipeline. **Note:** This notebook is designed for Google Colab. To run on Colab:
   - Upload the notebook to Google Colab
   - Mount your Google Drive
   - Modify `DRIVE_BASE` path in the Configuration cell to your Drive folder
   - Run all cells sequentially

