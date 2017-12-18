# Mon 18 Dec 2017

## Kaggle competition: web traffic time series forecasing

[Kaggle: web traffic time series forecasting](https://www.kaggle.com/c/web-traffic-time-series-forecasting)

Forecasting the future values of multiple time series - the goal is to forecast future web traffic for approximately 145,000 Wikipedia articles.

Complete freedom in how to produce your forecasts, just a few examples of possible approaches:

- use of univariate vs multi-variate models

- use of metadata (article identifier)

- hierarchical time series modeling (for different types of traffic)

- data augmentation (e.g. using Google Trends data to extend the dataset)

- anomaly and outlier detection and cleaning

- different strategies for missing value imputation

### Data

The training dataset consists of approximately 145k time series. Each of these time series represent a number of daily views of a different Wikipedia article, starting from July, 1st, 2015 up until December 31st, 2016. The leaderboard during the training stage is based on traffic from January, 1st, 2017 up until March 1st, 2017.

The second stage will use training data up until September 1st, 2017. The final ranking of the competition will be based on predictions of daily views between September 13th, 2017 and November 13th, 2017 for each article in the dataset. You will submit your forecasts for these dates by September 12th.

For each time series, you are provided the name of the article as well as the type of traffic that this time series represent (all, mobile, desktop, spider). You may use this metadata and any other publicly available data to make predictions. Unfortunately, the data source for this dataset does not distinguish between traffic values of zero and missing values. A missing value may mean the traffic was zero or that the data is not available for that day.

To reduce the submission file size, each page and date combination has been given a shorter Id. The mapping between page names and the submission Id is given in the key files.

### Approaches

- [Forum discussion on feature ideas and training](https://www.kaggle.com/c/web-traffic-time-series-forecasting/discussion/39395)
    - you can not really distinguish yearly seasonality from trend with 1.5 years of data.

- [Github code](https://github.com/gmontamat/web-traffic-time-series-forecasting)
    - contains useful links on background, kernels, and techniques

**2nd place winning solution**

Used a combination of deep learning and XGBoost, described in the [Kaggle discussion forum](https://www.kaggle.com/c/web-traffic-time-series-forecasting/discussion/39395).

What made that competition quite challenging is that some participants quickly found that the median of the visits for the previous 7 weeks was a very good predictor of future visits.  Doing better than that was quite challenging, and only 50 participants or so over 1,000 managed to beat the median benchmark.

Another difficulty was the [SMAPE (Symmetric Mean Absolute Percentage Error)](https://en.wikipedia.org/wiki/Symmetric_mean_absolute_percentage_error) metric used to evaluate submissions. SMAPE is a [weird metric](https://www.kaggle.com/cpmpml/smape-weirdness) because it is discontinuous at 0, and it is non convex.

- [2nd place winning solution](https://www.ibm.com/developerworks/community/blogs/jfp/entry/2nd_Prize_WInning_Solution_to_Web_Traffic_Forecasting_competition_on_Kaggle?lang=en)
    - [GitHub code](https://github.com/jfpuget/Kaggle/tree/master/WebTrafficPrediction)

**Towards data science blog article**

[Blog article](https://towardsdatascience.com/predicting-web-traffic-on-wikipedia-44004d6b152e)

[GitHub code](https://github.com/shubh24/web_traffic_prediction)

- The web traffic on 145K Wikipedia page is to be predicted for the period of Sept to Nov 2017

- The training data consisted of day-by-day view counts on the wiki pages, for the past two years.

- looked up the discussions/kernels on how the ARIMA models were performing
    — Apparently, auto-regressive models don’t generalize well to unknown ranges of the target variable (which is a very possible scenario in our problem)

- A couple approaches stood out:
    - Modelling the time-series problem as a regression problem, every page-date pair being treated as a row
    - Using Prophet by Facebook, their new forecasting tool

- On the advice of some top kagglers, i decided to take up the regression model
    - Melt the time-series based dataframe into a traditional page-date-features per row dataframe.
    - Run an xgb, and predict on a similarly melted test dataframe.

## Links

### Data Science

- [15 trending data science GitHub repositories for 2017](https://www.analyticsvidhya.com/blog/2017/12/15-data-science-repositories-github-2017/)

- [12 month data science learning plan](https://www.analyticsvidhya.com/blog/2017/01/the-most-comprehensive-data-science-learning-plan-for-2017/)
    - very good resources and layout for a structured learning plan with timescales for each period

- [Multicore processing in R and Python (video)](https://www.dominodatalab.com/resources/multicore-data-science-r-python/?utm_source=blog&utm_medium=post&utm_campaign=multicore-data-science-r-python)
    - [article excerpt from the full video with a good summary](https://blog.dominodatalab.com/multicore-data-science-r-python/)

- [Easy parallel loops in R and Python](https://blog.dominodatalab.com/simple-parallelization/)

**Time Series Analysis**

- [Medium articles on time series analysis](https://medium.com/tag/timeseries)

- [StitchFix: Reasoning about state in time series](http://multithreaded.stitchfix.com/blog/2017/07/13/inventory-time-machine/)

- [A comprehensive beginner’s guide to create a Time Series Forecast](https://www.analyticsvidhya.com/blog/2016/02/time-series-forecasting-codes-python/)
    - uses [example dataset of air passengers](https://www.analyticsvidhya.com/wp-content/uploads/2016/02/AirPassengers.csv) of monthly passenger numbers
    - example code in Python
    - prequel material [A complete tutorial on time series modeling in R](https://www.analyticsvidhya.com/blog/2015/12/complete-tutorial-time-series-modeling/)

- [WTF is time series (part 1)](https://towardsdatascience.com/statistics-is-freaking-hard-wtf-is-time-series-part-1-22a44300c64b)

- [WTF is time series (part 2)](https://medium.com/@NegiPrateek/statistics-is-freaking-hard-wtf-is-time-series-part-2-e9c5d2e72564)

[Forecasting time series through smoothing (part 1)](https://medium.com/@mauriciomaroto/smooth-to-forecast-anything-4de1948b1ef0)

[Forecasting time series through smoothing (part 2)](https://medium.com/@mauriciomaroto/you-can-make-forecasts-too-part-2-3c409c0b7255)

**Preparing approaches to a data science problem**

https://www.analyticsvidhya.com/blog/2016/09/how-to-prepare-for-your-first-data-science-hackathon-in-less-than-2-weeks/

1. **Get into a routine**
    - create a routine and follow it for at least 14 days

2. **Focus on fundamentals and business thinking for building features**
    - you don't need to try out every possible DS solution to find the best one
    - understand the problem well, think about the problem and real life scenarios to create features

3. **Learn the importance of building a hypotheses**
    - first thing you should do is gain functional domain knowledge
    - next (and maybe most important) is build a comprehensive list of hypotheses
    - build your hypotheses before actually looking at the distributions in the data
    - this removes bias of what you see in the data, and allows you to plan your workflow better
    - if you can think of hundreds of features, then prioritise which ones you would create first
    - also allows you to plan your time appropriately on data exploration, and imputation / missing value treatment

4. **Find complementary skills**
    - if you have been a coder all your life, team up with someone who has been on the business side of things
    - this helps get a more diverse set of hypotheses

5. **Prepare libraries of reusable code before hand**
    - if there are common steps in your workflow, keep code for these operations handy
    - e.g. turning dates into a variety of features

- [Data exploration guide](https://www.analyticsvidhya.com/blog/2016/01/guide-data-exploration/)
    - lays out various steps in data exploration and the analysis workflow

- Focus on feature engineering
    - [Dealing with categorical variables](https://www.analyticsvidhya.com/blog/2015/11/easy-methods-deal-categorical-variables-predictive-modeling/)
    - [Dealing with continuous variables](https://www.analyticsvidhya.com/blog/2015/11/8-ways-deal-continuous-variables-predictive-modeling/)

- [Common machine learning algorithms](https://www.analyticsvidhya.com/blog/2015/08/common-machine-learning-algorithms/)
    - [Improving the performnace of your ML models](https://www.analyticsvidhya.com/blog/2015/12/improve-machine-learning-results/)