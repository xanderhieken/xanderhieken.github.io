---
title: "PUBG Behavioral Analysis"
date: 2020-04-05
tags:
 - Python
 - Jupyter Notebook
 - SQL
 - SQLite
 - Spark
 - Behavioral Analysis
 - Data Warehousing
excerpt: "Identifying Areas to Improve Player Engagement"
header:
  overlay_image: "/assets/PUBGBackground.jpg"
  overlay_filter: 0.3 # same as adding an opacity of 0.3 to a black background
  teaser: "/assets/PUBGBackground.jpg"
  actions:
    - label: "Go to GitHub Repository"
      url: "https://github.com/xanderhieken/PUBG_BehavioralAnalysis"
---
# PlayerUnknown’s Battlegrounds Behavioral Analysis
**This analysis takes game and death data from over 720,000 games of PUBG to learn more about player behavior and help make recommendations to increase their engagement with the game.**

## The Data
This project uses the [PUBG Match Deaths and Statistics Dataset](https://www.kaggle.com/skihikingkevin/pubg-match-deaths) from Kaggle.

The dataset is comprised of player statistics from over 720,000 competitive matches, which is separated into two different collections- **Death Statistics** and **Aggregate Match Statistics**. 

Those collections are each split into five CSV files that are approximately 2 GB each, so I will not be including the data in the GitHub repository. Everything can still be downloaded from the link above, and the code will show you how to use PySpark to reduce the necessary disk space from over 20 GB to just under 6 GB to more comfortably fit everything into memory to work with.

![PUBG Data](https://xanderhieken.github.io/assets/PUBGdata.png)

## Video Presentation of the Process and Results
<iframe src="https://drive.google.com/file/d/1Essld83pqs3WCZJet2ll8RcMQaoBNdpF/preview" width="640" height="360"></iframe>

## Author
**Xander Hieken**

## Acknowledgements
* Keven Pei's [PUBG Match Deaths and Statistics](https://www.kaggle.com/skihikingkevin/pubg-match-deaths) dataset available on Kaggle
