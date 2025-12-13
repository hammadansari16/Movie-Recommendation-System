# Movie-Recommendation-System

This repository contains a machine learning project that builds a movie recommendation system. The system suggests movies similar to a user's selection by analyzing movie metadata such as genres, keywords, cast, and crew. It leverages Content-Based Filtering and Natural Language Processing (NLP) techniques.

📋 Project Overview
In the era of streaming platforms, recommendation engines are crucial for helping users discover content they enjoy. This project implements a content-based recommender that computes similarities between movies based on their textual attributes (tags). When a user selects a movie, the system recommends the top 5 most similar movies.

🛠️ Technologies Used
Python: Core programming language.

Pandas: For data manipulation and analysis.

NumPy: For numerical operations.

Ast: For processing stringified lists in the dataset.

NLTK: For stemming words to their root forms.

Scikit-Learn: For vectorization (CountVectorizer) and calculating cosine similarity.

Pickle: For saving the processed data and similarity matrix for deployment.

📂 Dataset
The project utilizes the TMDB 5000 Movie Dataset (available on Kaggle).

tmdb_5000_movies.csv: Contains movie details like budget, genres, homepage, id, keywords, original_language, original_title, overview, popularity, production_companies, release_date, revenue, runtime, spoken_languages, status, tagline, title, vote_average, vote_count.

tmdb_5000_credits.csv: Contains cast and crew information for each movie.

🚀 Methodology
Data Loading & Merging: The movies and credits datasets are loaded and merged on the movie title.

Feature Selection: Key columns are selected for building tags: movie_id, title, overview, genres, keywords, cast, and crew.

Data Preprocessing:

Handling Missing Values: Rows with null values are dropped.

Parsing JSON Columns: Helper functions convert stringified lists of dictionaries (genres, keywords, cast, crew) into clean lists of names.

Cast & Crew Filtering: Only the top 3 actors and the director are retained.

Text Cleaning: Spaces are removed from names (e.g., "Sam Worthington" -> "SamWorthington") to create unique tags.

Tag Creation: A tags column is created by concatenating the overview, genres, keywords, cast, and director.

Text Processing (Stemming): The PorterStemmer from NLTK is applied to the tags to reduce words to their base forms (e.g., "dancing" -> "danc").

Vectorization: The CountVectorizer converts the text tags into 5000-dimensional vectors, removing stop words.

Similarity Calculation: Cosine Similarity is computed between all movie vectors to measure their closeness.

Recommendation: A function takes a movie title, finds its index, sorts the similarity scores, and returns the top 5 similar movies.

📊 How it Works
The core idea is Content-Based Filtering. Every movie is represented as a vector in a multi-dimensional space based on its tags. The angle between these vectors (cosine similarity) determines how similar two movies are.

If you like Avatar, the system finds movies with vectors closest to Avatar's vector (e.g., Aliens, Guardians of the Galaxy).

