# Movie Recommendation System

**One-line summary:** A movie recommendation system built using MovieLens ratings data, comparing content-based filtering, collaborative filtering, and SVD. Collaborative filtering achieved the best Precision@10 (0.094) and NDCG@10 (0.118) among the evaluated models.

## Problem

Users often find it difficult to choose movies from a large collection. This project recommends movies based on movie content and user rating patterns.

## Data (Source, Licence, Size, Sparsity)

- **Source:** MovieLens `ml-latest-small`
- **Files:** `ratings.csv` and `movies.csv`
- **Ratings used:** 100,836
- **Movies:** 9,742
- **Users:** 610
- **Licence:** Check the official MovieLens dataset terms before redistribution.
- **Sparsity:** Most users have rated only a small fraction of all available movies.

## Method

- **Content-based filtering:** Uses movie titles and genres with TF-IDF and cosine similarity.
- **Collaborative filtering:** Uses similarities between users' rating patterns.
- **SVD:** Uses matrix factorization to estimate user preferences.
- **Data splitting:** Uses a chronological per-user split, keeping the latest ratings for testing.
- **Evaluation:** RMSE, Precision@10, Recall@10, and NDCG@10.

## Results

| Model | RMSE | Precision@10 | Recall@10 | NDCG@10 |
|---|---:|---:|---:|---:|
| Global mean | 1.067 | 0.000 | 0.000 | 0.000 |
| Most popular | N/A | 0.083 | 0.025 | 0.104 |
| Content-based | 1.057 | 0.050 | 0.011 | 0.053 |
| Collaborative | 1.065 | 0.094 | 0.025 | 0.118 |
| SVD | 1.065 | 0.083 | 0.007 | 0.086 |

Collaborative filtering performed best on Precision@10 and NDCG@10. Content-based filtering achieved the lowest RMSE among models with reported rating predictions.

**Demo screenshot:** Add a screenshot of the notebook showing recommendations generated for a user or a movie title.

## Understanding Pack

- **By-hand check:** Verify one collaborative-filtering prediction using the actual neighbour similarities, ratings, and means from the model.
- **Deliberate leakage:** Honest RMSE was 1.065; leaky RMSE was 1.0641. The small improvement illustrates how using test data can distort evaluation.
- **Break-it findings:** Test a new user, a movie with no rating history, and a user with only one rating. Document the observed results and fallback behaviour.

## Limitations

- The dataset is relatively small compared with real-world recommendation platforms.
- Ratings can be sparse, making recommendations difficult for new users and movies.
- Content-based recommendations use only titles and genres, so they do not capture deeper movie characteristics.
- Evaluation results depend on the chosen split and relevance threshold.
- A single evaluation split does not establish which model will perform best in every situation.

## AI-use Note

ChatGPT helped with code suggestions, debugging, recommendation methods, and evaluation explanations. I checked the dataset, ran the notebook cells, compared model metrics, and verified the recommendation outputs.

## How to Run

1. Open the project notebook in Google Colab.
2. Upload `ratings.csv` and `movies.csv` from the MovieLens dataset.
3. Run the notebook cells in order, from data loading through the recommendation demo.
4. Test recommendations using a user ID or a movie title.

**Environment:** Python, pandas, NumPy, scikit-learn, and Google Colab.
