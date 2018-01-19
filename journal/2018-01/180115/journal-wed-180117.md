# Wed 17 Jan 2018

[] Have a look at Kaggle housing datasets, maybe Zoopla, or Boston house prices?
    - scikit-learn has one built in for Boston house prices

[scikit-learn Boston house prices](https://archive.ics.uci.edu/ml/datasets/housing)

```python
from sklearn import datasets
data = datasets.load_boston()
print(data.DESCR) # prints data description (only works on scikit learn datasets)
```

## Links

- [A Beginner’s Guide to Data Engineering — Part I](https://medium.com/@rchang/a-beginners-guide-to-data-engineering-part-i-4227c5c457d7)

- [Cloud AutoML: Making AI acccessible to every business](https://www.blog.google/topics/google-cloud/cloud-automl-making-ai-accessible-every-business/)
    - [associated HN threads](https://news.ycombinator.com/item?id=16168098)

- [Random Forest tutorial to predict wine quality](https://elitedatascience.com/python-machine-learning-tutorial-scikit-learn)
    - really good explanatory tutorial, skips exploratory analysis to just focus on the steps and thought process behind them

- [Ensemble Machine Learning Algorithms in Python with scikit-learn](https://machinelearningmastery.com/ensemble-machine-learning-algorithms-python-scikit-learn/)
    - case study looking at Boosting, Bagging and Majority Voting

*Repeated from Thu 11 Jan 2018*

- Random Forest in Python
    - [1. A Practical End-to-End Machine Learning Example](https://towardsdatascience.com/random-forest-in-python-24d0893d51c0)
    - [2. Improving the Random Forest](https://towardsdatascience.com/improving-random-forest-in-python-part-1-893916666cd)
    - [3. Hyperparameter Tuning the Random Forest in Python](https://towardsdatascience.com/hyperparameter-tuning-the-random-forest-in-python-using-scikit-learn-28d2aa77dd74)