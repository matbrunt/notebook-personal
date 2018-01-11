# Thu 11 Jan 2018

Use the *Python Machine Learning* ebook as an introduction to a number of areas:

- Chapter 2: Training ML algorithms for Classification
    - Implementing a perceptron learning algorithm in Python
    - Minimising cost functions with gradient descent
    - Implementing an Adaptive Linear Neuron in Python
    - Stochastic gradient descent

- Chapter 9: embedding an ML model into a web application
    - Using SQLite as a data store
    - Turning a classifier into a web application
    - Serving via Flask

## ML Project, replicating stock market forecasting papers

Each paper uses a different algorithm and approach to forecast the direction a share price will take in a future window.

Try to implement each paper and come close to their results, then 

- provides a demonstration of using different algorithms

- allows comparison of techniques, with strengths and weaknesses

### Papers

- [Predicting the direction of stock market prices using random forest](https://arxiv.org/pdf/1605.00003.pdf)

- Algorithmic Trading Strategy Based On Massive Data Mining
    - Haoming Li, Zhijun Yang and Tianlun Li (2014)
    - *Algorithmic Trading Strategy Based On Massive Data Mining*. Stanford University.
    - linear classifier Logistic Regression, success rate of 55.65%

- Cuckoo Optimized SVM for Stock Market Prediction
    - Ms. K. Nirmala Devi, Dr.V.Murali Bhaskaran, G. Prem Kumar (2015).
    - IEEE Sponsored 2nd International Conference on Innovations in Information, Embedded and Communication systems (ICJJECS)2015

## Presenting Scientific Content

Will Ratcliffe posted a nice 2-pager of ideas on giving a [great scientific talk](https://www.dropbox.com/s/j1vv2baheiduvip/David%20Attenborough%20talk%20technique%202018.pdf?dl=0).

The core idea is that humans absorb information effortlessly if it is delivered as a compelling story. I call it the 'David Attenborough' method, in honor of the master.

> There are two things that have stuck with me from the course. First that there is always a story to tell. This story is almost never _“here are all the cool things I’ve tried and algorithms I’ve experimented with”_

> Second, you need to have a range. You don’t want to do every presentation in full on awestruck breathy voiced mode.

## Links

- [StackOverflow Jobs: Machine Learning Engineer (m/f) - Mid Level (python, pyspark, hadoop, docker)](https://stackoverflow.com/jobs/154588/machine-learning-engineer-m-f-mid-level-hellofresh)

- [FloydHub](https://www.floydhub.com), Deep Learning as a service platform

- [What's the difference between data science, machine learning, and artificial intelligence?](http://varianceexplained.org/r/ds-ml-ai/)
    - **Data science** produces **insights**
    - **Machine learning** produces **predictions**
    - **Artificial intelligence** produces **actions**

- [Science and data science](https://pdfs.semanticscholar.org/1110/9614dbc3f3214e6b80b8de14c7facd0bcea4.pdf)
    - Data science from three perspectives: statistical, computational, and human. 

- Machine Learning Fundamentals
    - [1. Cost Functions And Gradient Descent](https://dataflume.wordpress.com/2017/11/27/understanding-machine-learning-fundamentals-via-linear-regression/)
    - [2. Neural networks](https://towardsdatascience.com/machine-learning-fundamentals-ii-neural-networks-f1e7b2cb3eef)

- How to deploy machine learning models with TensorFlow
    - [1. Make your model ready for serving](https://towardsdatascience.com/how-to-deploy-machine-learning-models-with-tensorflow-part-1-make-your-model-ready-for-serving-776a14ec3198)
    - [2. Containerize it!](https://towardsdatascience.com/how-to-deploy-machine-learning-models-with-tensorflow-part-2-containerize-it-db0ad7ca35a7)
    - [3. Into the Cloud!](https://towardsdatascience.com/how-to-deploy-machine-learning-models-with-tensorflow-part-3-into-the-cloud-7115ff774bb6)
    - grew out of the [Udacity Deep Learning Foundations Nanodegree](https://www.udacity.com/course/deep-learning-nanodegree-foundation--nd101) materials
    - [Experiences from the Udacity Deep Learning foundation nanodegree](https://towardsdatascience.com/my-experience-with-udacity-deep-learning-foundations-nanodegree-a42a010f7b58)

- [No-Hassle Machine Learning Experiments with Azure Notebooks](https://towardsdatascience.com/no-hassle-machine-learning-experiments-with-azure-notebooks-e1a22e8782c3)

- Random Forest in Python
    - [1. A Practical End-to-End Machine Learning Example](https://towardsdatascience.com/random-forest-in-python-24d0893d51c0)
    - [2. Improving the Random Forest](https://towardsdatascience.com/improving-random-forest-in-python-part-1-893916666cd)
    - [3. Hyperparameter Tuning the Random Forest in Python](https://towardsdatascience.com/hyperparameter-tuning-the-random-forest-in-python-using-scikit-learn-28d2aa77dd74)

- [Monitoring your home network with InfluxDB on Raspberry Pi with Docker](https://medium.com/@petey5000/monitoring-your-home-network-with-influxdb-on-raspberry-pi-with-docker-78a23559ffea)
    - Covers running Docker on a RaspberryPi 3, with InfluxDB, Telegraf, and Grafana containers
    - InfluxDB is a time series db platform
    - Telegraf is part of the InfluxDB platform, acts as an agent for collecting and reporting metrics and events
    - Grafana is dashboard for time series analytics

- Progressing to be a real data scientist
    - [Imposter syndrome](https://brohrer.github.io/imposter_syndrome.html)
    - [Interviewing](https://brohrer.github.io/get_data_science_job.html)
    - [Building a project](http://brohrer.github.io/one_step_program_become_data_scientist.html)

- [Python module search path](https://docs.python.org/3/tutorial/modules.html#the-module-search-path)
    - saving this here so I can find it when I've forgotten again