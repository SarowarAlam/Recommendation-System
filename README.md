1. Introduction
The goal of this project is to implement a recommendation system using Content-Based Filtering and Collaborative Filtering techniques. As an example the system leverages the MovieLens dataset to recommend movies based on movie content or user preferences.

2. Dataset Overview
The MovieLens dataset includes two files:

movies.csv:

movieId: Unique identifier for each movie.
title: The movie title and release year.
genres: A pipe-separated list of movie genres.
ratings.csv:

userId: Unique identifier for each user.
movieId: The ID of the rated movie.
rating: The user's rating for the movie, on a scale of 0.5 to 5.
timestamp: The time the rating was provided (not used in this implementation).
3. Methodology
3.1 Content-Based Filtering
Content-based filtering recommends movies similar to a user's preferred movie by analyzing movie features (e.g., title and genres).

Steps:
Feature Engineering:

The title and genres columns are combined into a new content column for each movie.
TF-IDF Vectorization:

The content column is vectorized using TF-IDF (Term Frequency-Inverse Document Frequency) to convert text into numerical vectors.
TF-IDF emphasizes rare and important terms, reducing the weight of common words.
Cosine Similarity:

Computes cosine similarity between movies' TF-IDF vectors, quantifying how similar movies are based on their content.
Recommendation Function:

For a given movie_title, retrieves similar movies using cosine similarity scores.
Returns the top 5 most similar movies.
Example Recommendation:
For the movie "Toy Story (1995)", the system identifies movies with similar genres or themes.

3.2 Collaborative Filtering
Collaborative filtering predicts user preferences by leveraging the ratings of users with similar preferences.

Steps:
Dataset Preparation:

The ratings dataset is formatted for the Surprise library, defining the rating scale (0.5 to 5) using the Reader class.
Train-Test Split:

The dataset is split into training (75%) and testing (25%) sets.
SVD Model:

Trains an SVD (Singular Value Decomposition) model on the training set.
Learns latent features that represent users and movies to predict user ratings.
Evaluation:

The model is tested on the test set, and its performance is evaluated using RMSE (Root Mean Squared Error).
Recommendation Function:

For a given user_id, identifies unrated movies and predicts their ratings.
Returns the top 5 movies with the highest predicted ratings.
Example Recommendation:
For user_id=1, the system suggests movies the user is likely to enjoy based on ratings from other users with similar preferences.

4. Results
4.1 Content-Based Recommendations
For "Toy Story (1995)", the system recommends movies with similar content, such as:

"Toy Story 2 (1999)"
"A Bug's Life (1998)"
"Monsters, Inc. (2001)"
"Finding Nemo (2003)"
"The Incredibles (2004)"
4.2 Collaborative Filtering Recommendations
For user_id=1, the system recommends movies based on predicted ratings, such as:

"The Matrix (1999)"
"Inception (2010)"
"The Dark Knight (2008)"
"Pulp Fiction (1994)"
"Forrest Gump (1994)"
4.3 Model Evaluation
RMSE (Collaborative Filtering):
The RMSE score for the SVD model on the test set was approximately 0.7753.
This low RMSE indicates that the model predicts user ratings with high accuracy.
5. Limitations
Content-Based Filtering:

Only considers movie metadata (title and genres).
Cannot recommend movies with different themes or genres.
Ignores user preferences and past behavior.
Collaborative Filtering:

Requires sufficient user rating data to make accurate predictions.
Struggles with the cold start problem for new users or movies with no ratings.
Data Size:

Due to resource constraints, only the first 10,000 movies were used for testing.
6. Future Improvements
Hybrid Recommendation System:

Combine content-based and collaborative filtering to leverage the strengths of both.
Deep Learning:

Use neural networks, such as autoencoders, to capture more complex patterns in user behavior.
Context-Aware Recommendations:

Incorporate contextual information, such as time, location, or user demographics.
Expanded Metadata:

Enrich movie features with additional attributes (e.g., director, cast, reviews).
7. Conclusion
This project demonstrates the application of Content-Based Filtering and Collaborative Filtering in building a movie recommendation system. Content-based filtering effectively identifies movies similar to a user's preferred movie, while collaborative filtering provides personalized recommendations based on user behavior. The SVD model's RMSE score of 0.7753 highlights its accuracy and potential for real-world applications. Together, these approaches form a robust foundation for advanced recommendation systems.
