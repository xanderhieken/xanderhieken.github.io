---
title: "Hockey Hall of Fame Predictions"
date: 2019-11-03
tags:
 - Python
 - R
 - Jupyter Notebook
excerpt: "Using Career Statistics for NHL Players to Predict Future Inductees to the Hockey Hall of Fame"
header:
  overlay_image: "/assets/HOFBackground.jpg"
  overlay_filter: 0.3 # same as adding an opacity of 0.3 to a black background
  teaser: "/assets/HOFBackground.jpg"
  actions:
    - label: "Go to GitHub Repository"
      url: "https://github.com/xanderhieken/HockeyHOFPredictions"
---

# Exploratory Data Analysis and Predictive Modeling for the Hockey Hall of Fame

**This study visually explores career NHL statistics before building a model to predict which players will get into the Hockey Hall of Fame.**

## The Data
I used the `NHL.csv` file that is located in the data folder of the GitHub repository for this study.

The dataset contains cumulative statistics for the careers of 1914 players in the NHL.

## The Process
I start this project by importing the data and creating histograms, bar charts, and scatterplots for the different features to help visually explore the data.

In order to better compare the distribution of each feature for Hall-of-Famers vs Non Hall-of-Famers, I generated a parallel coordinates plot that shows pretty significant stratification:

![Parallel Coordinates](https://xanderhieken.github.io/assets/ParallelCoord.png)

This let me know that Hall-of-Famers are actually (mostly) statistically different from their peers, which means I should be able to make some fairly accurate predictions using this data.

After checking distributions and correlations of the data, I reduced the dataset to only include players with a minimum of 500 career games played, which removed a lot of the clutter. The number of total records reduced from 1914 to 764 after this adjustment, so I created the following scatterplots to see how things looked now.

>These scatterplots show the relationship between games played and six statistics that are highly correlated to Hall of Fame induction.
>
>The size of each datapoint is based on that player's career plus/minus (bigger is better)
>
>Players that are already in the Hall of Fame appear much darker in color

![Scatterplots](https://xanderhieken.github.io/assets/HHOFScatterplots.jpg)

At this point, I knew that I would be using logistic regression to make binary predictions, so I split the data into training and testing sets.

>* Total Records: 764
>
>	* Training: 611
>
>		* 568 Out
>
>		* 43 In
>
>	* Testing: 153
>
>		* 136 Out
>
>		* 17 In

## Results
As it turns out, there is a reason those players made it into the Hall of Fame- they've separated themselves from the rest of the pack, both statistically and metaphorically.

Aside from three false negative predictions, the other 150 records in the test data were correctly classified:

![Classification Report](https://xanderhieken.github.io/assets/HHOFCR.png)

Since the overwhelming majority of the data is for players that aren't currently in the Hall of Fame, and I would prefer a balance of precision and recall, **F1** is going to be the best metric to use. 

At the end of the day, there really aren't that many players that have ever made it into the Hockey Hall of Fame. After exploring the data, it's a lot more obvious that the players who are in the Hall of Fame usually make a very strong case for themselves by continuing to play at a high level for many years. The minimum of 500 career games that I used for this project is the equivalent of playing just over six full NHL seasons without missing a single game, and it's even more common to see a Hall-of-Famer play over 1,000 games before hanging up their skates!

## Author
**Xander Hieken**
