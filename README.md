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

### Regarding aap.py file

The Python file you've uploaded is a script for a web-based movie recommender system built with Streamlit, a popular library for creating data applications. This script appears to offer a user-friendly interface for users to get movie recommendations along with movie posters. Here's a detailed breakdown of its structure and functionality:

### Introduction

This script implements a movie recommender system that provides users with movie recommendations based on their preferences. It utilizes Streamlit for the frontend, allowing users to interact with the application through a web interface. The system uses a dataset of movies and a similarity metric stored in pickle files to find and suggest movies that are similar to the user's choice. Additionally, it fetches and displays movie posters from an external API, enhancing the user experience by providing visual context for each recommendation.

### Details

**Key Components and Workflow:**

- **Streamlit Interface**: The script uses Streamlit to create a web interface, making it accessible and easy to use. The title of the application is set to "Movie Recommender System," and it prompts the user to select a movie they like from a dropdown menu populated with movie titles.

- **Movie Recommendations**: Upon selecting a movie and clicking the "Recommend" button, the system computes recommendations based on the selected movie. This is done by looking up the movie in a preloaded DataFrame created from a dictionary of movies (`movie_dict.pkl`), calculating similarity scores using a preloaded similarity matrix (`similarity.pkl`), and then selecting the top movies that are most similar to the chosen one.

- **Fetching Movie Posters**: For each recommended movie, the script fetches its poster using the `fetch_poster` function. This function makes an HTTP request to the TMDB API (The Movie Database) using a specific movie ID, retrieves the movie details, and constructs a URL to the movie's poster image.

- **Displaying Recommendations**: The recommended movies and their posters are displayed in a row of columns, making efficient use of Streamlit's layout capabilities. Each column shows the movie title and its poster, providing a visual and descriptive recommendation to the user.

- **Pickle Files**: The system relies on two pickle files for its operation. The `movie_dict.pkl` file contains a dictionary representation of the movie dataset, and `similarity.pkl` stores the similarity matrix. These files are loaded at runtime, enabling the recommender system to quickly access precomputed data.

### Conclusion

This Streamlit application demonstrates an effective use of Python for building interactive data applications. By combining the simplicity of Streamlit with the power of machine learning and data processing, it offers an engaging way for users to discover movies similar to their tastes. The inclusion of movie posters fetched from an external API further enriches the user experience, making the recommendations more tangible and visually appealing.

In conclusion, the movie recommender system showcases a comprehensive approach to recommending movies by leveraging machine learning techniques and data processing to analyze movie metadata and identify similar movies based on user preferences.
