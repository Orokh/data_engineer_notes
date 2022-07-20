---
creation date: 2022-05-23 16:36
tags:
---

# Algorithms

![[Pasted image 20220429110430.png|700]]

```mermaid
graph LR
	%% Nodes
	s1["There is a historical right answer (Supervised ML)"]
	s2["I'm just exploring (Unsupervised ML)"]
	s3["I want to forecast a number (e.g. future sales)"]
	s4["Try Linear Regression"]
	s5["I want to classify something"]
	s6["Binary (buy/no buy)"]
	s7["Try Logistic Regression"]
	s8["Multi-Class (high, medium, low risk)"]
	s9["Try Logistic Regression with multi class option"]
	s10["I want to recommend something"]
	s11["Try Matrix Factorization"]
	s12["Try Clustering"]
	
	%% Links
	s1-->s3
	s3-->s4
	s1-->s5
	s5-->s6
	s6-->s7
	s5-->s8
	s8-->s9
	s1-->s10
	s10-->s11
	s2-->s12


	%% Styling
	classDef blue fill:#4285F1;
	classDef red fill:#EA433F;
	classDef yellow fill:#FABB06;
	classDef green fill:#33A951;
	
	class s1,s2 blue
	class s3,s5,s10 red
	class s6,s8 yellow
	class s4,s7,s9,s11,s12 green
```

## Classification

Advanced models:

- #dnn (Deep Neural Networks) - Model non-linear relationships in the data (ex: car price evaluation)
- Gradient boosted trees / #xgboost - Iteratively fit a decision tree to the residuals of preceeding decision trees

## Regression

- DNN Regression - Non linear regression
- XGBoost

## Matrice factorization

Used to create recommendations for users

## K-means clustering

Unsupervised

Explore paterns in the data by grouping data into cluster

Utility: get insights from clustering with statistics analysis to identify what's special about each cluster

# Methods

## Anomaly detection

> #anomaly #detection also known as #outlier detection is the process of finding data points within a dataset that differs from the rest. Common applications of anomaly detection includes fraud detection in financial transactions, fault detection and predictive maintenance.
> Broadly speaking, anomaly detection can be categorized into _#supervised_ and _#unsupervised_ realm. Supervised anomaly detection requires labelled dataset that indicates if a record is “normal” or “abnormal”. Unsupervised anomaly detection involves an unlabeled dataset. It assumes that the majority data points in the unlabeled dataset are “normal” and it looks for data points that differs from the “normal” data points.

[Source](https://towardsdatascience.com/unsupervised-anomaly-detection-in-python-f2e61be17c2b)

## Reinforcement learning

> #reinforcement learning is a method based on rewarding desired behaviors and/or punishing undesired ones. In general, a reinforcement learning agent is able to perceive and interpret its environment, take actions and learn through trial and error.

[Source](https://www.techtarget.com/searchenterpriseai/definition/reinforcement-learning)

## Overfitting

Overfitting is when a model is so close to its training data that it cannot adapt to the data used for prediction.

The tools to prevent overfitting: less variables, regularization, early ending on the training.

- Adding more training data will increase the complexity of the training set and help with the variance problem.
- Reducing the feature set will ameliorate the overfitting and help with the variance problem.
- Increasing the regularization parameter will reduce overfitting and help with the variance problem.

### Methods

#### Regularization

Use L1 regularization when you need to assign greater importance to more influential features. It shrinks less important feature to 0.

L2 regularization performs better when all input features influence the output & all with the weights are of equal size.

Parametrization of regularization is very important. If the parameter is too high, the model becomes too simple and tends to *underfit*. On the other hand, if the parameter is too low, the effect of regulatization becomes negligible and the model is likely to *overfit*.

#### Dropout methods

Used for neural networks

#### Dimensionailty reduction

Used for normal md models
