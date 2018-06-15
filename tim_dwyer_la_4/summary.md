# Outcomes

The two questions in mind here are as follows:
> Q1: How can we distinguish between the whose score is the median and those whose score is below the median?

> Q2: Given the recent questions regarding the truth of what we read and see online, it is helpful to try to create machine algorithms which could flag content of questionable authority. With this is mind I will propose a method for building a machine learning model predicting whether an author has expertise in a subject.


## Summary for Q1

After processing the collected Reddit threads we fit some Logistic Regression models, K-Nearest neighbors classifiers, Decision Trees and Random Forests. After tuning we found the following table of accuracy rates (percentage of  testing data correctly classified) for those models.


|model|baseline| Logistic Regression| K-Nearest neighbors | Decision Tree | Random Forest
|------|
|accuracy on test data | 50%| 63.88%| 76.90%| 80.21%| 75.39%|

From this we suggest the use of the decision tree model which can be found, as a pickle file, in the directory [models/](./models).

## Summary for Q2

|class| Baseline Accuracy| K-Nearest Neighbors Accuracy | Decision Tree Accuracy | Random Forest Accuracy
|-|
|`datascience`| 67.19%| 68.91% | 79.34% | 79.62%
|`math`| 53.58% | 63.97% | 86.35% | 83.71%
|`python`| 61.80%| 58.18% | 83.07% | 79.85%

On the collected data, the Decision Tree model is the best at telling the difference between posts from a subreddit about a topic and posts from a subreddit about learning that topic. To continue with this method of trying to detect subject matter expertise we could, in the future, try grouping subjects together grouped by expertise level. We have stored our pickled models, for future comparison, in [models/](./models).
