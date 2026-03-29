#  Movie Recommendation System — Jacaranda Movie Shop

A collaborative, content-based, and hybrid movie recommendation system built for **Jacaranda Movie Shop** to improve user engagement, personalization, and retention.


##  Project Overview

This project builds and evaluates three recommendation approaches:

- **Content-Based Filtering** — recommends movies similar in title and genre using TF-IDF + cosine similarity
- **Collaborative Filtering (SVD)** — latent factor model that predicts ratings based on user-item interactions
- **Item-Based KNN** — memory-based model finding movies similar to those a user rated highly
- **Hybrid Recommender** — blends SVD and KNN scores (60/40 weighting) for stronger personalized recommendations


##  Dataset

The project uses the [MovieLens](https://grouplens.org/datasets/movielens/) dataset with the following files:

| File | Description |
|---|---|
| `movies.csv` | Movie titles and genres |
| `ratings.csv` | User ratings (userId, movieId, rating, timestamp) |
| `links.csv` | IMDb/TMDb links per movie |
| `tags.csv` | User-applied tags per movie |


##  Requirements

Install dependencies with:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```


##  Notebook Structure

| Section | Description |
|---|---|
| Business Understanding | Goals and success criteria for Jacaranda Movie Shop |
| Data Loading & EDA | Load all CSVs, explore ratings, users, genres |
| Feature Engineering | Extract movie year, combine title + genre as content features |
| Visualizations | Top movies/genres by rating count and average rating |
| Content-Based Model | TF-IDF vectorizer + cosine similarity on movie content |
| Model 1 — SVD | TruncatedSVD collaborative filtering with RMSE/MAE evaluation |
| Model 2 — KNN | Item-based KNN using cosine similarity |
| Hybrid Recommender | Weighted blend of SVD + KNN predictions |



##  Usage

### Content-Based Recommendations

```python
# Get movies similar to a given movieId
get_similar_movies(movieId=1, top_n=10)
```

### SVD Recommendations (Collaborative Filtering)

```python
# Get top 5 recommendations for a user
recommend_svd(user_id=1, top_n=5)
```

### KNN Recommendations (Item-Based)

```python
# Get top 5 personalized recommendations for a user
recommend_knn(user_id=1, top_n=5)
```

### Hybrid Recommendations

```python
# Blend SVD and KNN for stronger recommendations
hybrid_recommender(user_id=42, movie_ids=candidate_movies, svd_weight=0.6, knn_weight=0.4, top_n=5)
```



##  Model Evaluation

| Model | RMSE | MAE | Notes |
|---|---|---|---|
| SVD | 2.004 | 1.544 | Useful for ranking, less precise on absolute ratings |
| KNN | — | — | Explainable; similarity-based scoring |
| Hybrid | Best | Best | Outperforms either model alone on Precision@5 |


##  Key Insights

- Most highly rated movies have very few ratings — popularity ≠ quality
- Rating distribution is approximately normal (mean ≈ median)
- The hybrid model improves overall recommendation precision compared to either SVD or KNN alone
- KNN recommendations are interpretable: *"We recommended Die Hard because you liked similar action movies"*


##  Business Context

Built for **Jacaranda Movie Shop** with the following goals:

- Increase watch time and user engagement
- Improve satisfaction through personalized suggestions
- Reduce churn by making the platform more "sticky"
- Drive revenue growth through relevant content discovery
