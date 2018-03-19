# Mon 12 Mar 2018

[Rolling-origin validation](https://www.otexts.org/fpp/2/5)

If you find that performance is a bottleneck, you could do subsampling. Don't use every possible origin. Instead, use, e.g., every fifth possible origin. (Make sure you don't introduce unwanted confounding between your subsampled origins and seasonality in the data. For instance, if you use daily data, don't use every seventh day as an origin, because then you are really only assessing forecasting quality on Tuesdays, or only on Thursdays etc.)

Then again, you don't really need to train your model again from scratch every time you roll the origin forward. Start out from the last trained model. (For example, in Exponential Smoothing, simply update your components with the new data since the last training.) This should dramatically cut down on your overall training time.


[Time series cross-validation](https://robjhyndman.com/hyndsight/tscvexample/)

## Links

- [Case study in evaluating time series prediction models using the relative mean absolute error](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5270768/)

- [ML for Product Managers: Problem Mapping](https://towardsdatascience.com/machine-learning-for-product-managers-part-i-problem-mapping-5436132c3a6e)

- [ML for Product Managers: ML Skills](https://towardsdatascience.com/machine-learning-for-product-managers-part-ii-ml-skills-ce7c3cee3246)