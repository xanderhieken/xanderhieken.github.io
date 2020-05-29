---
title: "Movie Recommendation Engine"
date: 2019-11-08
tags:
 - Python
 - Spark
 - JSON
 - Jupyter Notebook
 - SQL
 - SQLite
 - Text Analysis
 - Natural Language Processing
excerpt: "How to Build a Movie Recommendation Engine with Spark"
header:
  overlay_image: "/assets/MovieRecommendationsBackground.jpg"
  overlay_filter: 0.3 # same as adding an opacity of 0.3 to a black background
  teaser: "/assets/MovieRecommendationsBackground.jpg"
  actions:
    - label: "Go to GitHub Repository"
      url: "https://github.com/xanderhieken/MovieRecommendations"
---

# Building a Movie Recommendation Engine in Spark

**This notebook shows how to use collaborative filtering in Spark to analyze user ratings and create a movie recommendation engine**

## The Data
Data for this project comes from the small [MovieLens](https://grouplens.org/datasets/movielens/) dataset that is recommended for education and development. 

These files contain a total of 100,846 movie ratings from 610 unique users for 9,742 movies. 

Both files necessary for this project can be found in the data folder of the GitHub repository, so you don't need to download the full ZIP that includes additional unnecessary files:

* `movies.csv`

	* Three features: `movieId `, `title`, and `genre`

* `ratings.csv`

	* Four features: `userId`, `movieId`, `rating`, and `timestamp`

## The Process
After loading the data into Spark DataFrames, I split the ratings into testing and training sets of 80% and 20%, respectively:
```python
(trainingRatings, testRatings) = ratings.randomSplit([0.8, 0.2])
```

Spark uses Alternating Least Squares for collaborative filtering, so to build the model, these are the settings I used:
```python
als = ALS(userCol='userId', itemCol='movieId', ratingCol='rating', coldStartStrategy="drop")
```
>Note that `coldStartStrategy = "drop"` is used account for new users and movies that the model hasn't trained on.

After setting that up, it's time to train and test the model:
```python
model = als.fit(trainingRatings)
predictions = model.transform(testRatings)
```
## Results
To evaluate the performance of the model, I used Spark's `RegressionEvaluator` function:
```python
evaluator = RegressionEvaluator(metricName='rmse', labelCol='rating', predictionCol='prediction')

evaluator.evaluate(predictions)
```

The Root Mean Squared Error (RMSE) for the ALS model is: **0.8792733496088538**

Since all the ratings range from 0.5 to 5.0, an RMSE of ~0.88 shows very little promise for making accurate predictions.

Even though the predicted ratings might not be the most accurate, let's take a look at the top ten predictions for user 133 to see the output:

![Movie Recommendations](https://xanderhieken.github.io/assets/MovieRecs.png)


## Author
**Xander Hieken**

## Acknowledgements
**[MovieLens](https://grouplens.org/datasets/movielens/) Data from GroupLens Research**
* F. Maxwell Harper and Joseph A. Konstan. 2015. The MovieLens Datasets: History and Context. ACM Transactions on Interactive Intelligent Systems (TiiS) 5, 4: 19:1–19:19. [https://doi.org/10.1145/2827872](https://doi.org/10.1145/2827872)
