# Thu 04 Jan 2018

> To start, focus on what things DO, not what they ARE.

[?] Micheal Jordan, "Bag of Little Bootstraps" talk.

**FastAI Learning path**

1. Machine Learning for Coders

2. Deep Learning for Coders Part 1 (revised edition in PyTorch)

3. Deep Learning for Coders Part 2 (still in TensorFlow)

4. Computational Linear Algebra for Coders

## FastAI: Machine Learning for Coders

### Lesson 2

Continue from 1:04:00

[Lesson 2: YouTube (video)](https://www.youtube.com/watch?v=blyXCk4sgEg&feature=youtu.be)

[Lesson 1: Notebook](https://github.com/fastai/fastai/blob/master/courses/ml1/lesson1-rf.ipynb)

[GitHub repo](https://github.com/fastai/fastai/tree/master/courses/ml1)

When you get a negative $$R^2$$ value, it's not a bug - it means your model is worse at predicting than if you just used the mean all the time.

What's the ratio between how good your model is, and how good the naive mean error model is.

Don't need to remember the formula, just the meaning behind it.

Always have a validation set - creating this is the most important thing when building the modeling process in an an ML project.

If your data has a time component, i.e. can be used as a time series, you tend to split at a point in time.

On Kaggle, if you submit too many times, you will just end up overfitting to the leaderboard.

Prefix model fit step with `%time`, then it will tell you how long it actually took to train the model (wall time is real elapsed time).

```python
m = RandomForestRegressor(n_jobs=-1)
%time m.fit(X_train, y_train)
print_score(m)
```

If something takes >10 seconds to run, it becomes harder to work with it in an interactive fashion. To reduce the training time randomly sample X rows to train and iterate on, then once happy with a general approach, at the end of the day you can run the longer model training on the full data set.

In scikit-learn, an individual tree in a forest is called an *estimator*.

## Links

## Data Science

- [FastAI: Computational Linear Algebra for Coders](https://github.com/fastai/numerical-linear-algebra)
    - [Blog post](http://www.fast.ai/2017/07/17/num-lin-alg/)
    - assumes more background than *Practical Deep Learning for Coders* course
    - recommends watching [3Blue 1Brown Essence of Linear Algebra](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) as preparation if new to Linear Algebra

- [FastAI: Deep Learning for Coders - full notes and transcripts](http://www.fast.ai/2017/02/24/captions-and-notes/)
    - [Course notes](http://wiki.fast.ai/index.php/Course_notes)

## Software Engineering

[Improving your data science workflow with Docker](https://unsupervisedpandas.com/data-science/docker-for-data-science/)

[Amazon EC2 Spot lets you pause and resume your workloads](https://aws.amazon.com/about-aws/whats-new/2017/11/amazon-ec2-spot-lets-you-pause-and-resume-your-workloads/)

## Adhoc

- [Jeremy Howard on Language Acquisition Performance](http://quantifiedself.com/2012/05/jeremy-howard-on-language-acquisition-performance/)
    - studying Chinese for last 2 years
    - uses spaced repetitive learning, found in SuperMemo and Anki