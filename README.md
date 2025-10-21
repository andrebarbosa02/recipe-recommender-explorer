# Recipe Recommender & Analysis

> Ever wondered how ingredients connect across cuisines?

This Jupyter Notebook project explores the world of recipe data through a combination of machine learning, network analysis, and natural language processing. By analyzing similarities between recipes based on their ingredients, we build a weighted graph of recipes and generate personalized recommendations, all while uncovering trends, patterns, and insights across thousands of dishes.

---

## Project Overview

This project combines several machine learning and data science techniques to explore and recommend recipes:

- **Social Network Analysis**: Recipes are modeled as nodes in a weighted graph. Edges represent ingredient similarity — the more ingredients two recipes share, the stronger their connection.
- **Recommender Systems**: Suggest similar recipes based on content (ingredients) or user preference patterns.
- **Natural Language Processing & Topic Modeling**: Ingredients and titles are processed using NLP techniques. Topic modeling (LDA and TSNE) is used to uncover hidden themes across recipes.
- **Time Series Forecasting**: A popularity score is engineered from recipe features and forecasted over time using Auto ARIMA to understand trends and seasonality.
- **Exploratory Data Analysis**: Ingredient distributions, recipe types, and user behavior are analyzed for insights.

---

## Technologies & Libraries

- Python (Jupyter Notebook)
- pandas, numpy, matplotlib, seaborn
- igraph (for graph and clusters creation)
- nltk / spaCy (for NLP preprocessing)
- scikit-learn (LDA and TSNE included)
- statsmodels (Auto ARIMA)


---

## Project Structure

This project is developed entirely in a **Jupyter Notebook**, and organized into the following sections:

1. **Data Loading & Cleaning**  
   Preprocessing of recipes, members, reviews and ingredient data. The dataset is [Hummus](https://gitlab.com/felix134/connected-recipe-data-set), containing three csv files: `members.csv`, `recipes.csv` and `reviews.csv`. Those were connected using the ids available.

2. **Ingredient Similarity Graph**  
   Construct a weighted graph where recipes are nodes and edges are based on shared ingredients, using a tf-idf approach to create the weights of ingredients sharing importance. The more common the ingredients were, the less relevant they were to being shared.
   Creation of clusters and selection of biggest one to apply the recommendation system.
   Extensive analysis of metrics related to Social Network Analysis, such as Closeness, Eccentricity, Connectivity, etc.

4. **Recommendation System**  
   Suggest similar recipes based on recipes similarity when applying an item-based recommendation system. When using a user-based recommendation system, selection of recipes ratings and reviews to associate another recipe to that user. For content-based filtering, use of recipe description for recipe similarity.
   Manual evaluation of the performance of the recomendation systems, depending on whether suggested recipes were considered relevant or not, with precision at k.
   Models used: KNN and SVD.

6. **Topic Modeling & NLP**  
   Ingredients processing with NLP to improve performance on dataset cleaning. Application of uniformization (lowercase, removing extra characters), weighting of best process between lemmatization, stemming and tokenization, selection between count and tf-idf vectorizer
   For Topic Modelling, Latent DirichletAllocation (LDA) and t-Distributed Stochastic Neighbor Embedding (TSNE) applications to split recipes by ingredients in different topics with identification of most relevant words per topic, either by tf-idf methodology (not the best due to gathering irrelevant words for cuisine) or most frequent ones.

8. **Popularity Score & Time Series**
   Temporal analysis of reviews and decomposition analysis to detect any trend, seasonality or residual data.
   Create a custom popularity score and forecast it over time using Auto ARIMA. Popularity score created according to correlation between reviews count, likes and rating with following distribution:
     ```
     weights = {
      'rating': 0.2,
      'likes': 0.4,
      'review_count': 0.4,
      'likes_to_reviews_ratio': 0.1,
      'likes_to_rating_ratio': 0.1
     }
     ```
   Evaluation using a train and test dataset and selection of best Auto ARIMA performing model.


---

## Limitations

- The notebook is intended for **technical users** and not packaged as a web app or API.
- Some parameters must be manually adjusted in the notebook to test new recipes or change recommendation settings.

---

## Example Use Cases

- Get recipe suggestions based on shared ingredients
- Analyze how popularity of certain recipe types may evolve
- Explore how recipes are clustered by ingredients and topics

---

