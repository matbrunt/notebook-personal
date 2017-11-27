# Fri 24 Nov

## Pros/Cons of staying in current role

What are the benefits of staying here?

- access to knowledgable staff

- mentoring from Ewan

What are the negatives of working here?

- no travel opportunities, regardless what the PR says

- more interested in hiring graduates and training them, than training more experienced staff

- walled garden for data science work, only available to the clique

- day to day duties are predominantly engineering

## Investment data product

Can use this as a showcase iterative project.

Gather initial data, won't get everything I need, just enough to do the next piece of work, rather than a big upfront push, e.g. waterfall.

As work progresses and I want to add new features I'll discover what data I need for them. At that point I can go back and backfill the data I need.

Which is a typical workflow in business, we'll get some data for a job. A while later someone will ask for different data and we'll need to backfill existing records with the new data points.

As long as I keep the original raw scrapes, I can reprocess them for additional data without having to generate new scrapes.

When I need new data points not in the archives I can fire off new scrapers.

## Using openscoring to productionise an ML model

[Openscoring: REST web service for scoring PMML models](https://github.com/openscoring/openscoring)

Web service that serves ML models serialised to JPMML (Java flavoured PMML files). Allows you to treat the ML model as a deployable unit in its own microservice, then communicate with it via http through an API interface.

PMML is the standard way to serialise ML models; Spark, scikit-learn, R, models can all be converted, and it lets you abstract away the language.

Possible architecture:

```
client > Web API > Openscoring REST service
                      ^
      serialised model in the form of a JPMML file
                      ^
      scikit-learn/Spark to JPMML converter
                      ^
      scikit-learn (or Spark) pipeline
```

Airbnb have written a nice article on a pipeline implementation similar to this: [Architecting a machine learning system for risk](https://medium.com/airbnb-engineering/architecting-a-machine-learning-system-for-risk-941abbba5a60)

There are also libraries to perform the conversion:

[jpmml-sparkml](https://github.com/jpmml/jpmml-sparkml)

[jpmml-sklearn](https://github.com/jpmml/jpmml-sklearn)

[jpmml-r](https://github.com/jpmml/jpmml-r)

[Java library and command-line application for converting TensorFlow models to PMML](https://github.com/jpmml/jpmml-tensorflow)

[sklearn-porter - transpile trained scikit-learn estimators to C, Java, JavaScript etc](https://github.com/nok/sklearn-porter)

## Links

### Machine Learning

[Openscoring: REST web service for scoring PMML models](https://github.com/openscoring/openscoring)

[Deploying deep learning models to production via TensorFlow serving and Kubernetes](https://www.tensorflow.org/serving/serving_inception)

### Visualisation

[Tableau: Creating a stacked bar chart for multiple measures](http://kb.tableau.com/articles/howto/stacked-bar-chart-multiple-measures)