# Wed 13 Dec 2017

```
adict = {'open': 'first', 'high':'max', 'low':'min', 'close' : 'last'}

ohlc_vol = data.groupby(['volcumgrp'])['price'].agg(adict)
```

## Links

### Machine Learning

- http://www.argmin.net/2017/12/05/kitchen-sinks/
    - TLDR, "we don't know anything"
    - "Having magical things that work well without us understanding them will get us quite far. When we really start to understand why these things work, then we're going to get even more gains." Ewan
    - NIPS 2017 paper "Random Features for Large-scale Kernel Machines"

- [Interpretable Machine Learning: A Guide for Making Black Box Models Explainable.](https://christophm.github.io/interpretable-ml-book/)
    - excellent ebook resource about making interpretable machine learning models
    - place in top list of useful ML links
    - "going to be an increasingly important subject, with more legislation around ML based products, and the ethical questions that they're starting to raise." Ewan

[A curated list of awesome Machine Learning frameworks, libraries and software.](https://github.com/josephmisiti/awesome-machine-learning)

### Data Analysis

- [Bitcoin transactions on blockchain visualised in VR](https://github.com/bitcoin-vr/bitcoin-vr)
    - Data visualisation using virtual reality
    - Built using React-VR

- [12 Useful Pandas Techniques in Python for Data Manipulation](https://www.analyticsvidhya.com/blog/2016/01/12-pandas-techniques-python-data-manipulation/)
    - Some very useful examples of pivot, crosstab, binning and coding nominal data