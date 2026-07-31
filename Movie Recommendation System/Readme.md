# Content-Based Movie Recommendation System

## Project Overview
This project is a Content-Based Movie Recommendation System built using Python, Pandas, and Scikit-Learn. It recommends movies similar to a user-provided movie title based on attributes like genres, keywords, cast, and the director.

## Dataset
* **Source:** [Kaggle - TMDB 5000 Movie Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
* **Description:** Contains metadata for around 5000 movies from The Movie Database (TMDb), including budget, revenue, cast, crew, genres, and overviews.

## Environment
This project is designed to be executed in **Google Colab**.

## Prerequisites
* A Kaggle account and an API token (`kaggle.json`) to download the dataset.

## Workflow Pipeline
1. **Data Acquisition:** Configures the Kaggle API and downloads the TMDb 5000 movies and credits datasets.
2. **Data Merging & Selection:** Merges the `movies` and `credits` dataframes based on the movie title. Filters down to essential columns (`movie_id`, `title`, `overview`, `genres`, `keywords`, `cast`, `crew`).
3. **Feature Engineering:**
   * Uses `ast.literal_eval` to extract names from JSON-formatted string columns (genres, keywords).
   * Extracts the top 3 actors from the `cast` column.
   * Extracts the 'Director' from the `crew` column.
   * Removes spaces from all extracted names/keywords to treat multi-word entities (like "Science Fiction" or "Johnny Depp") as single unique tags.
4. **Tag Creation:** Concatenates all processed textual data into a single `tags` column.
5. **Stemming & Vectorization:** * Applies PorterStemmer to reduce words to their root forms.
   * Uses Scikit-Learn's `CountVectorizer` to convert the text tags into a 5000-dimensional bag-of-words vector matrix, filtering out standard English stop words.
6. **Similarity Calculation:** Computes the Cosine Similarity between all movie vectors.
7. **Recommendation Engine:** A custom function that takes a movie title, finds its corresponding vector, sorts all other movies based on cosine similarity scores, and outputs the top 5 closest matches.

## Usage
1. Open a new Google Colab notebook.
2. Ensure you have your `kaggle.json` file ready to upload when the first cell prompts you.
3. Paste the code blocks sequentially into separate cells and run them from top to bottom.