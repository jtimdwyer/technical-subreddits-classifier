# Distinguishing Between Technical Subreddits
_By Tim Dwyer_

### Problem Statement

In this repository I've explored two basic questions.

> Q1: How can we distinguish between the whose score is the median and those whose score is below the median?

For this we will collect some information about reddit posts and see if we can build a nice classifier model that, based on the data collected, predicts whether a post does or does not have a score higher than the median score.

> Q2: Given the recent questions regarding the truth of what we read and see online, it is helpful to try to create machine algorithms which could flag content of questionable authority. With this is mind I will propose a method for building a machine learning model predicting whether an author has expertise in a subject.

To this end, we collect data from some subreddits which have explicit topics and a corresponding subreddit with a bend towards learning about that topic.


| Topic Subreddit | Learning Subreddit |
|--|--|
| `r/math` | `r/learnmath`  |
| `r/python` | `r/learnpython`  |
| `r/datascience` | `r/learnmachinelearning`  |

We will ultimately construct a few models for each of these three classification problems and analyze the results.

### File Structure
```
.
├── README.md
├── data/
└── notebooks/
```

The `data/` directory is where the `csv` and `json` files are stored after being obtained through the Reddit and Pushshift APIs, as well as the staging ground for files throughout data processing.

The `notebooks/` directory contains a number of Jupyter notebooks that detail the data collection, exploration and modeling process.

### Outline
1. [Data collection](./notebooks/1_data_acquisition.ipynb)
    > For the first question I obtained around 10,000 posts on the default `all` page of reddit by querying the official Reddit API. For the second question I sent requests to the Pushshift API. For each subreddit, I obtained the first 500 (if there were that many) posts for every hour of every day in the year 2017. Typically there are many fewer posts in a given hour, so while its likely that we have a lot of missing posts, this is still a fairly typical sample of activity on the subreddits. In a second notebook the raw json objects obtained from these queries is converted to csv files for easier handling by Pandas. Primary tools: Requests, Pandas, Pushshift API, Reddit API

2. Data Exploration
    > There are two notebooks for this, [the first](./notebooks/3a_exploration) for Q1 and [the second](./notebooks/3b_exploration) for Q2. These notebooks contain some analysis about the distributions of the numerical features that were collected. Some of the data is transformed to remove skew in the hopes of improving the performance of some Logistic Regression models. Primary tools: Pandas, Seaborn

3. Modeling
    > Again we have two notebooks for [Q1](./notebooks/4a_modeling.ipynb)  and [Q2](./notebooks/4b_modeling.ipynb) to separate out the two threads of inquiry. We fit and tune a number of Logistic regression models, K-nearest neighbors classifier, Decision Trees and Random Forests. Primary tools: SKLearn, Pandas

4. [Summary and Conclusions](./notebooks/summary.md)
    > This file contains an overview and summary of the results of our modeling and analysis.
