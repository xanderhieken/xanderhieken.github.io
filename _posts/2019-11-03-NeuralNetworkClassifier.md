---
title: "Neural Network Classifiers"
date: 2019-11-03
tags:
 - Python
 - Jupyter Notebook
 - Text Classification
 - Image Classification
 - Neural Networks
 - Keras
 - Scikit-learn
excerpt: "How Build Neural Network Classifiers for Text and Images"
header:
  overlay_image: "/assets/NeuralBackground.png"
  overlay_filter: 0.3 # same as adding an opacity of 0.3 to a black background
  teaser: "/assets/NeuralBackground.png"
  actions:
    - label: "Go to GitHub Repository"
      url: "https://github.com/xanderhieken/NeuralNetworkClassifier"
---
# Building Neural Network Classifiers for Text and Images

**This notebook shows how build neural networks using Scikit-learn and Keras to classify text and images.**

## The Data
* Part 1 of this project uses `categorized-comments.jsonl`:
	* Contains 450,000 rows with two columns- category (`cat`) and text (`txt`)

* Part 2 of this project uses the MNIST dataset included in Keras:
	* You can import the data directly into testing and training sets using this code: 
```python
from keras.datasets import mnist
(X_train, y_train), (X_test, y_test) = mnist.load_data()
```
## Tasks

### Part 1: Text Classification
1. Build a neural network with Scikit-learn

2. Build a neural network with Keras

3. Use the neural networks to classify Reddit comments into one of four categories:

	a. News
	
	b. Science and Technology
	
	c. Sports
	
	d. Video Games 
	
4. Report each model's accuracy, precision, recall, F1, and confusion matrix

### Part 2: Image Classification
1. Load the MNIST dataset from Keras into testing and training sets

2. Reshape and rescale the images to feed into the model

3. Build a neural network with Keras

4. Train and test the model

5. Report the model's accuracy and loss

## Results
Below, you can find the accuracy for each model, but you can find the remainder of the evaluation metrics in the Jupyter Notebook located in this project's [GitHub repository](https://github.com/xanderhieken/NeuralNetworkClassifier). 

#### Text Classification
Scikit-learn Accuracy: 0.61725

Keras Accuracy: 0.64225

#### Image Classification
Keras Accuracy: 0.9855999946594238

## Author
**Xander Hieken**
