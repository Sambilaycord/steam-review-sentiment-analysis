# Steam Review Sentiment & Player Behavior Analysis

![Python](https://img.shields.io/badge/Python-3.9%2B-blue) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Supabase-336791) ![Scikit-Learn](https://img.shields.io/badge/ML-Scikit--Learn-orange) ![Status](https://img.shields.io/badge/Status-Completed-success)

## Project Overview
**What factors influence how players review games on Steam?**

This project is an end-to-end data mining and machine learning pipeline that investigates the relationship between player engagement metrics (playtime, library size) and review sentiment. By extracting over **10,000 reviews** via the Steam Web API and warehousing them in a **Supabase (PostgreSQL)** database, we identified distinct behavioral patterns between "casual" positive reviewers and "veteran" negative critics.

The project culminates in a **Logistic Regression** model that predicts review sentiment with **92% accuracy** based on lexical features.

## Key Features & Pipeline

This project moves beyond static CSV analysis by implementing a robust **ETL (Extract, Transform, Load)** workflow:

1.  **Data Extraction:** Automated fetching of review data for the Top 10 most-reviewed Steam games using the `Steam Web API`.
2.  **Relational Storage:** Architected a normalized **PostgreSQL** schema on **Supabase** to ensure data integrity.
3.  **In-Database Processing (ELT):** Utilized **SQL Stored Procedures and Views** to handle cleaning, deduplication, and feature engineering (e.g., calculating `playtime_ratio`) directly within the database layer.
4.  **Sentiment Analysis:** Trained a **Logistic Regression** model (TF-IDF vectorization) to classify reviews, optimizing for class imbalance.

## Tech Stack

* **Languages:** Python, SQL (PostgreSQL)
* **Data Engineering:** Supabase, Steam Web API, Pandas, JSON
* **Machine Learning:** Scikit-Learn (Logistic Regression, TF-IDF), NLTK
* **Visualization:** Matplotlib, Seaborn

## Key Findings

Through Exploratory Data Analysis (EDA), we uncovered several "Business Insights" regarding player psychology:

* **The Engagement Gap:** Positive reviewers have significantly higher median playtime (**60 hours**) compared to negative reviewers (**41.5 hours**).
* **The "Parting Shot" Theory:** A `playtime_ratio` of **1.0** (Playtime at Review / Total Playtime) is a strong predictor of negative sentiment. This indicates players often "Rage Quit"—writing a negative review immediately before uninstalling the game forever.
* **The "Veteran" Critic:** Negative reviews tend to be **2x longer** and come from users who own **3x more games**. Experienced players are harsher critics.
* **Model Performance:** Our NLP model achieved **92% Accuracy**, identifying that functional words (*crash, update, boring*) drive negative sentiment, while experiential words (*fun, love, peak*) drive positive sentiment.

## Repository Structure

```bash
├── PHASE_1.ipynb   # API Selection & Data Strategy
├── PHASE_2.ipynb   # Database Architecture & ETL (Loading to Supabase)
├── PHASE_3.ipynb   # SQL Preprocessing (Stored Procedures & Views)
├── PHASE_4.ipynb   # EDA & Machine Learning (Sentiment Prediction)
├── PHASE_5.ipynb   # Final Report & Synthesis
├── requirements.txt # Python dependencies
└── README.md
```
## Installation & Usage

1.  **Clone the repository**
    ```bash
    git clone [https://github.com/yourusername/steam-sentiment-analysis.git](https://github.com/yourusername/steam-sentiment-analysis.git)
    ```

2.  **Install Dependencies**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Environment Setup**
    Create a `.env` file in the root directory with your API credentials:
    ```env
    STEAM_API_KEY=your_steam_key
    SUPABASE_URL=your_supabase_url
    SUPABASE_KEY=your_supabase_key
    ```

4.  **Run the Analysis**
    Execute the Jupyter notebooks in sequential order to replicate the pipeline:
    * `PHASE_1.ipynb` (Data Collection)
    * `PHASE_2.ipynb` (Database Migration)
    * `PHASE_3.ipynb` (SQL Preprocessing)
    * `PHASE_4.ipynb` (Model Training)
    * `PHASE_5.ipynb` (Final Report)

