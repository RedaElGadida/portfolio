# Movie Recommendation System

## Project Overview

This project demonstrates how to build a robust movie recommendation system using the classic MovieLens 1M dataset. The analysis moves beyond a single modeling technique to explore the implementation of a **Content-Based** model, a **Collaborative Filtering** model (using SVD), and the concept of a **Hybrid System**.

## The Challenge: Sparsity & The "Cold Start" Problem

A primary challenge for recommendation engines is data sparsity and the "cold start" problem—how do you make good recommendations for new users or new movies with little to no historical data? This project explores how different models can address this challenge.

## Dataset

This project utilizes the **MovieLens 1M Dataset**.
-   It contains 1,000,000 ratings from 6,040 users on 3,706 movies.
-   The data is spread across three files: `ratings.dat`, `movies.dat`, and `users.dat`.

## Methodology

This project implements and evaluates two primary recommendation models:

1.  **Model 1: Content-Based Filtering:**
    * This model recommends movies based on their features. It calculates the similarity between movies using their genres (processed with `TfidfVectorizer`) and finds items that are similar to a user's known preferences using cosine similarity.

2.  **Model 2: Collaborative Filtering (SVD):**
    * This model uses the **Singular Value Decomposition (SVD)** algorithm, a powerful matrix factorization technique, to identify latent user and item factors. It recommends movies based on the tastes of similar users.
    * The model was built and evaluated using the `surprise` library.

3.  **Hybrid System Concept:**
    * A hybrid function was developed to conceptually combine the outputs of both models, aiming to provide recommendations that are both relevant (from content) and personalized (from user taste).

## Key Findings & Evaluation

The collaborative filtering model was established as the primary benchmark and was quantitatively evaluated on its ability to create a high-quality ranked list of recommendations.

-   **Average Precision@10: 87.3%** - On average, nearly 9 out of the 10 movies recommended to a user were relevant and liked by them.
-   **Average Recall@10: 36.8%** - The model successfully identified over a third of all movies a user would have enjoyed within its top-10 list.

These strong metrics validate the effectiveness of the SVD-based collaborative filtering approach. The project also highlighted the importance of a rigorous and fair evaluation framework when considering more complex hybrid systems.

## Technologies Used

-   **Language:** Python
-   **Libraries:**
    -   Pandas & NumPy
    -   Scikit-learn (for `TfidfVectorizer` and `cosine_similarity`)
    -   Surprise (for SVD implementation)
-   **Environment:** Jupyter Notebook / VS Code

## How to Run This Project

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    ```
2.  **Install dependencies:**
    ```bash
    pip install pandas numpy scikit-learn scikit-surprise
    ```
3.  **Run the notebook:**
    Open the `Movie-Recommender.ipynb` (or your chosen name) file in Jupyter Notebook and run the cells sequentially.

## Future Improvements

-   **Deep Learning:** Implement a more advanced model using neural networks (e.g., using Keras or PyTorch) for matrix factorization.
-   **Incorporate More Features:** Enhance the models by including user data (age, gender, occupation) or more movie metadata.
-   **Deployment:** Deploy the hybrid model as a simple interactive web application using Streamlit or Flask.