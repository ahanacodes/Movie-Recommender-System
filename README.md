# Movie-Recommender-System

### Introduction

The movie recommender system is designed to analyze a dataset of movies, including their genres, keywords, cast, and crew, to make personalized movie recommendations. The system employs a combination of Python libraries such as NumPy, pandas, and scikit-learn to preprocess the data, extract relevant features, and apply machine learning algorithms for recommendation. The core of the system relies on the cosine similarity measure to identify movies that are similar to a user's preferences, offering a more tailored recommendation compared to traditional methods.

### Detailed Description

**Data Acquisition and Preprocessing:**
- The system begins by loading two datasets: `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv`, which contain detailed information about movies and their credits, respectively.
- Here is alink to download dataset from Kaggle: https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata
- It then merges these datasets on the movie title to consolidate all relevant information into a single DataFrame.
- A series of data preprocessing steps are undertaken, including the removal of missing values and duplicates, ensuring the data is clean and ready for analysis.

**Feature Extraction:**
- The system focuses on extracting meaningful features from the datasets, specifically the genres, keywords, cast, and crew fields. To make these features usable for machine learning, it converts them from JSON-like string representations into a list of strings.
- This conversion is achieved through a custom `convert` function that parses the stringified JSON and extracts the names of genres, keywords, cast members, and crew members.

**Vectorization and Similarity Computation:**
- After preprocessing, the system consolidates all relevant features into a single 'tags' column that combines genres, keywords, cast, and crew into a unified text field for each movie.
- This 'tags' field is then vectorized using the `CountVectorizer` to transform the textual data into numerical vectors, facilitating the computation of similarity between movies.
- The cosine similarity metric is employed to calculate the similarity between all movies based on their vectorized feature representations. This approach helps to overcome the challenges posed by high-dimensional data.

**Recommendation Logic:**
- The recommendation function takes the title of a movie as input and identifies similar movies based on the cosine similarity scores. It ranks these movies and returns the titles of the top recommendations.
- This function demonstrates the system's ability to provide personalized movie suggestions by leveraging the computed similarities between movies.

**Persistence:**
- The final part of the notebook involves persisting the processed DataFrame, the movie dictionary, and the similarity matrix using the `pickle` library. This enables the recommender system to quickly load preprocessed data and similarity scores without the need to recompute them, enhancing the efficiency of the recommendation process.

In conclusion, the movie recommender system showcases a comprehensive approach to recommending movies by leveraging machine learning techniques and data processing to analyze movie metadata and identify similar movies based on user preferences.
