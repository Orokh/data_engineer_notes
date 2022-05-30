---
creation date: 2022-05-04 17:01

tags: gcp
---

[https://cloud.google.com/bigquery-ml/docs/introduction](https://cloud.google.com/bigquery-ml/docs/introduction)

# Cheatsheet

**Label**: alias a column as `label` or specify column in OPTIONS using `input_label_cols`

**Feature**: passed through to the model as part of your SQL `SELECT` statement.

```SQL
select * from ml.feature_info(model `mydataset.mymodel`)
```
	
**Model**: an object created in [[bigquery]] that resides in your dataset

**Model Types**: Linear Regression, Logistic regression, ...

```SQL
create or replace model <dataset>.<name>
options(model_type='<type>') as
<training dataset>
```

**Training progress**

```SQL
select * from ml.training_info(model `mydataset.mymodel`)
```
	
**Inspect weights**

```SQL
select * from ml.weights(model `mydataset.mymodel`, (<query>))
```

**Evaluation**

```SQL
select * from ml.evaluate(model `mydataset.mymodel`)
```

**Prediction**

```SQL
select * from ml.predict(model `mydataset.mymodel`, (<query>))
```
	
https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-syntax-create

Types of models:

- LINEAR_REG
- LOGISTIC_REG
- KMEANS
- MATRIX_FACTORIZATION
- TENSORFLOW

# Sample questions

What is regularization? L1 vs L2?

Possible to train on TF, and predict with BQ. When the model is stored in [[gcs]]
