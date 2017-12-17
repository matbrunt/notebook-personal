# Fri 15 Dec 2017

## Links

### Pandas

[Understanding the Transform Function in Pandas](http://pbpython.com/pandas_transform.html)

- [apply vs transform on groupby objects](https://stackoverflow.com/questions/27517425/apply-vs-transform-on-a-group-object)
      - apply implicitly passes all the columns for each group as a DataFrame to the custom function, while transform passes each column for each group as a Series to the custom function
      - The custom function passed to apply can return a scalar, or a Series or DataFrame (or numpy array or even list). The custom function passed to transform must return a sequence (a one dimensional Series, array or list) the same length as the group.

- [Python Data Science Handbook: aggregation and grouping](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/03.08-Aggregation-and-Grouping.ipynb)
    - Jupyter notebook from Jake VanderPlas book

[Weighted average functions in Pandas](http://pbpython.com/weighted-average.html)