# Movie Recommendation System — Jacaranda Movie Shop

This project is a movie recommendation system built using the **MovieLens dataset** from the GroupLens Research Lab (University of Minnesota).

The goal is simple but powerful:  
 **Recommend the top 5 movies a user is most likely to enjoy based on their past ratings.**

---

## Project Background

In real-world platforms like Netflix or Amazon Prime, users are often overwhelmed by the number of available choices. Without guidance, users may struggle to find content they actually enjoy.

This project simulates that real-world scenario for **Jacaranda Movie Shop**, where we aim to:

- Personalize user experience
- Improve content discovery
- Increase engagement and watch time
- Reduce churn by keeping users interested

---

## Problem Statement

Given a dataset of user ratings, the system should:

✔ Learn user preferences  
✔ Identify patterns between users and movies  
✔ Recommend **Top 5 movies** tailored to each user

> Note:  
> This is not just about “popular movies” — it’s about **relevant movies for each individual user**.

---

## Dataset

We use the MovieLens dataset:

https://grouplens.org/datasets/movielens/

> Recommendation:  
> Use the **“small” dataset (100k ratings)** if working locally to avoid performance issues.

### Files Used

| File          | Description                          |
| ------------- | ------------------------------------ |
| `movies.csv`  | Movie titles + genres                |
| `ratings.csv` | User ratings (core of the system)    |
| `links.csv`   | External IDs (not heavily used here) |
| `tags.csv`    | User-generated tags                  |

---

## Approach

This project explores multiple recommendation strategies, starting from the required baseline and building up to more advanced techniques.

---

### 1️ Collaborative Filtering (Core Requirement)

This is the **main method used in the system**.

- Based on user–item interactions
- Learns from patterns in user ratings
- Implemented using **Matrix Factorization (SVD)**

Idea:

> “Users who liked similar movies in the past will like similar movies in the future.”

---

### 2️ Content-Based Filtering

- Uses **movie metadata (title + genres)**
- Converts text into vectors using **TF-IDF**
- Computes similarity using **cosine similarity**

Useful when:

- A user is new (cold start)
- No rating history exists

---

### 3️ Hybrid Recommendation System

To improve performance, we combine:

- Collaborative filtering (SVD)
- Content-based filtering
- Popularity signals

This helps balance:

- Accuracy
- Diversity
- Cold-start handling

---

## Workflow Overview

```text
User Ratings → Data Processing → Feature Engineering → Model Training → Recommendations
```
