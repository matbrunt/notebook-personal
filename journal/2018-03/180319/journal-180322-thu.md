# Thu 22 Mar 2018

## Evaluating Time Series Predictions

[Creating a Seasonal Naive model for time series forecasting in Python](https://machinelearningmastery.com/seasonal-persistence-forecasting-python/)

We will use a walk-forward validation to evaluate model performance. This means that each time step in the test dataset will be enumerated, a model constructed on historical data, and the forecast compared to the expected value. The observation will then be added to the training dataset and the process repeated.

Finally, forecasts will be evaluated using root mean squared error, or RMSE. The benefit of RMSE is that it penalizes large errors and the scores are in the same units as the forecast values

### ARIMA

[Creating an ARIMA model for time series forecasting in Python](https://machinelearningmastery.com/arima-for-time-series-forecasting-with-python/)

If the time series shows a clear trend this suggests that the time series is not stationary and will require differencing to make it stationary, at least a difference order of 1.

## Analytics Consultant Job Description

### Analytics Consultant - Edinburgh

Excellent opportunity for an experienced Analytics professional with a leading client in Edinburgh. This will suit someone with recent experience in building modelling / analytics solutions.

### Role Profile:

- Working with clients on key data science & analytics projects

- Applying advanced analytics techniques to solve business problems: predictive modelling, linear / logistic regression, customer segmentation, decision trees, clustering, text analytics, speech analytics, time series

- Developing analytical solutions to support customer retention, marketing campaign targeting, customer next best action, customer experience, customer acquisition, demand / channel management, customer profitability / value, HR / People Analytics

- Create and deliver high quality presentations for clients

### Skills/Experience Required:

- Strong background in customer insight analytics

- SQL, SAS, Excel, VBA

- R or Python nice to have

- Excellent communication and presentation skills

- Experience working with large customer data sets

- Financial services experience nice to have but not mandatory

## Links

- [Building minimal Docker containers for Python applications](https://blog.realkinetic.com/building-minimal-docker-containers-for-python-applications-37d0272c52f3)

- [Getting your data science models into Production with Docker](https://medium.com/@gijswobben/data-science-in-production-with-docker-b6673231677a)
    - [Github repo with full code](https://github.com/gijswobben/docker_and_data_science)

- [Networking with Docker: Don't settle for the defaults](https://netbeez.net/blog/networking-with-docker/)

- [Sidecar logging pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/sidecar)

- [Building a productive Docker development environment](https://nrempel.com/guides/docker-development-environment/)
    - Nice example of building a PostgreSQL, Node.js, RabbitMQ and Redis stack
    - Good examples of using a manage shell script to admin the instances as well

- [Seasonal Naive forecast with Python](https://machinelearningmastery.com/seasonal-persistence-forecasting-python/)

