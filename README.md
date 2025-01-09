# Movie Recommendation System 

## **Overview**

This project implements a **Movie Recommendation System** using two techniques:
1. **Content-Based Filtering**: Recommends movies similar to a given movie by analyzing its content, such as title and genres.
2. **Collaborative Filtering**: Suggests movies based on user preferences and ratings using a matrix factorization technique.

---

## **Technologies Used**
- **Python**: Primary programming language for implementation.
- **Pandas**: For data manipulation and preprocessing.
- **Scikit-learn**: For vectorization and similarity computation in Content-Based Filtering.
- **Surprise**: For Collaborative Filtering using the SVD (Singular Value Decomposition) model.
- **TF-IDF**: To convert text features (title and genres) into numerical data for similarity computations.

---

## **Dataset**
This project uses the **MovieLens dataset**, which is a benchmark dataset for recommendation systems.

### **Dataset Details**
1. **movies.csv**:
   - `movieId`: Unique identifier for each movie.
   - `title`: Movie title with release year.
   - `genres`: Genres associated with the movie (pipe-separated).

2. **ratings.csv**:
   - `userId`: Unique identifier for each user.
   - `movieId`: ID of the rated movie.
   - `rating`: User rating on a scale from 0.5 to 5.0.

Dataset link: [MovieLens](https://grouplens.org/datasets/movielens/)

---

## **Project Features**

### **1. Content-Based Filtering**
**Objective**: Recommend movies similar to a given movie based on its metadata (title and genres).

**Methodology**:
1. Combine the `title` and `genres` into a single feature (`combined_features`).
2. Use **TF-IDF vectorization** to convert textual data into numerical form.
3. Compute pairwise **cosine similarity** between movies based on the TF-IDF vectors.
4. Recommend the top 5 movies with the highest similarity scores.

**Example**:  
For the movie `"Toy Story (1995)"`, the system recommended:
- **Toy Story 2 (1999)**
- **Toy, The (1982)**
- **We’re Back! A Dinosaur’s Story (1993)**
- **NeverEnding Story, The (1984)**
- **Monsters, Inc. (2001)**

---

### **2. Collaborative Filtering**
**Objective**: Suggest movies to a user based on their rating history and patterns observed in other users' ratings.

**Methodology**:
1. Train the **SVD (Singular Value Decomposition)** model on the ratings dataset.
2. Predict ratings for movies that the user has not rated.
3. Sort the predicted ratings and recommend the top 5 movies with the highest predicted scores.

**Evaluation**:
- The model achieved an **RMSE (Root Mean Squared Error)** of **0.7756**, which indicates a good level of accuracy in predicting user preferences.

**Example**:  
For `user_id=1`, the system recommended:
- **Alien (1979)**
- **Psycho (1960)**
- **Jaws (1975)**
- **Thing from Another World, The (1951)**
- **All That Heaven Allows (1955)**

---

## **Results Summary**

| **Technique**            | **Example Input**          | **Recommendations** (Top 5 Movies)                       |
|--------------------------|---------------------------|---------------------------------------------------------|
| Content-Based Filtering  | Toy Story (1995)          | Toy Story 2 (1999), Toy (1982), NeverEnding Story (1984), Monsters, Inc. (2001) |
| Collaborative Filtering   | User ID: 1               | Alien (1979), Psycho (1960), Jaws (1975), All That Heaven Allows (1955)         |

---

## **Limitations**
1. **Content-Based Filtering**:
   - Relies only on the movie's metadata (title and genres) and cannot consider user-specific preferences.
   - Cannot recommend movies that are dissimilar in content but highly rated by the user.

2. **Collaborative Filtering**:
   - Struggles with the **cold start problem**, as it requires sufficient data on new users or movies.
   - Predictions are limited to the scope of the training data (existing user-movie interactions).

3. **Data Constraints**:
   - For testing purposes, only the first 10,000 movies were used.

---

## **Future Improvements**
1. **Hybrid Recommendation System**:
   - Combine Content-Based and Collaborative Filtering techniques for better recommendations.
2. **Deep Learning**:
   - Use neural networks (e.g., autoencoders) to extract deeper relationships between users and movies.
3. **Enhanced Metadata**:
   - Include additional attributes like director, cast, reviews, and user demographics to improve recommendation accuracy.
4. **Context-Aware Recommendations**:
   - Factor in contextual information, such as time of day or user location.

---

## **Usage**
To replicate this project:
1. Download the [MovieLens dataset](https://grouplens.org/datasets/movielens/).
2. Update the dataset file paths in the script to point to the correct location on your system.
3. Install required Python libraries:
   ```bash
   pip install pandas scikit-learn surprise
   ```
4. Run the script and test the recommendations.

---

## Contact
If you have any questions or need further assistance, please feel free to contact:

- **Name**: Sarowar Alam
- **Email**: sarowaralam40@gmail.com
- **GitHub**: [https://github.com/SarowarAlam](https://github.com/SarowarAlam)

