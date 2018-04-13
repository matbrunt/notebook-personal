# Thu 29 Mar 2018

## DeepAR AWS Recurrent Neural Network model for time series forecasting

[SageMaker: DeepAR algorithm for more accurate time series forecasting](https://aws.amazon.com/blogs/machine-learning/now-available-in-amazon-sagemaker-deepar-algorithm-for-more-accurate-time-series-forecasting/)

> Forecasting is an entry point to applying machine learning across many industries. Whether it’s optimizing the supply chain through better product demand forecasts, allocating computing resources more effectively by predicting web server traffic, or saving lives by staffing hospitals to meet patient needs, there are few domains where investments into accurate forecasts don’t return their investments quickly.

> DeepAR is a supervised learning algorithm for time series forecasting that uses recurrent neural networks (RNN) to produce both point and probabilistic forecasts.

**Cold start forecasting**

> A cold start scenario occurs when we want to generate a forecast for a time series with little or no existing historical data. This occurs frequently in practice, such as in scenarios where new products are introduced or new AWS Regions are launched. Traditional methods such as ARIMA or ES rely solely on the historical data of an individual time series, and as such they are typically less accurate in the cold start case. Consider the example of forecasting clothing items such as sneakers. A neural network-based algorithm such as DeepAR can learn typical behavior of new sneaker sales based on the sales patterns of other types of sneakers when they were first released. By learning relationships from multiple related time series within the training data, DeepAR can provide more accurate forecasts than the existing alternatives.

**Probabilistic forecasts**

> DeepAR also produces both point forecasts (e.g., the amount of sneakers sold in a week is X) and probabilistic forecasts (e.g., the amount of sneakers sold in a week is between X and Y with Z% probability). The latter forecasts are particularly well-suited for business applications such as capacity planning, where specific forecast quantiles are more important than the most likely outcome. For example, a system that automatically places orders for sneakers based on the forecast might want to generate order quantities such that the warehouse is stocked to satisfy customer demand with X% probability.

Customers can leverage this functionality by specifying the appropriate likelihood function hyperparameter and specifying the desired quantiles at time of inference.

**Getting Started**

> DeepAR trains a model based on observed historical data, which is then used to perform predictions. Just like other Amazon SageMaker algorithms, it relies on Amazon Simple Storage Service (Amazon S3) to store the training data and the resulting model. Amazon SageMaker automatically starts and stops Amazon Elastic Compute Cloud (Amazon EC2) instances on behalf of customers during training. After the model is trained, it can be deployed to an endpoint that will compute predictions when requested.

DeepAR supports two types of data files: JSON Lines (one JSON object per line) and Parquet.

Refer to [DeepAR documentation](https://docs.aws.amazon.com/sagemaker/latest/dg/deepar.html) for detail on both options.

## Links

- [Writing a rekognition app in under two hours](https://medium.com/mint-digital/i-wrote-a-facial-rekognition-app-in-under-two-hours-b20d589e763d)
    - also combines React and Electron to implement as a desktop app

- [Using AWS SageMaker linear regression to predict store transactions](http://mitrai.com/tech-guide/using-aws-sagemaker-linear-regression-to-predict-store-transactions/)
    - using linear regression for time series forecasting
    - tries naive, one step ahead, multi step ahead methods
