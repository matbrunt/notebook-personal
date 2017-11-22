# Tue 21 Nov 2017

- estimated release date for revised FastAI course in PyTorch is January

- TensorFlow has released a dynamic execution option now called *Eager Execution*

- build into learning path pre-knowledge of neural networks, ready to take the course in January

> we strongly believe that the focus in learning needs to be on understanding the underlying techniques and how to apply them in practice, and how to quickly build expertise in new tools and techniques as they are released.

- look at using druid.io as datastore for financial data, with superset data platform on top to visualise

## Links

### Machine Learning

[10 things that can go wrong training a neural network](http://theorangeduck.com/page/neural-network-not-working)

[OpenAI: PPO implementation](https://blog.openai.com/openai-baselines-ppo/)

[OpenAI: Evolution strategies](https://blog.openai.com/evolution-strategies/)

[DeepMind: Reward Hacking, Emergence of locomotion behaviours in rich environment](https://deepmind.com/blog/producing-flexible-behaviours-simulated-environments/)

[arXiv: Deep Reinforcement Learning that matters](https://arxiv.org/pdf/1709.06560.pdf)

[OpenAI: Better exploration with parameter noise](https://blog.openai.com/better-exploration-with-parameter-noise/)

- [FastAI: What you need to do deep learning](http://www.fast.ai/2017/11/16/what-you-need/)
  - read this properly and turn into an article write up

- [FastAI: Introducing PyTorch for FastAI](http://www.fast.ai/2017/09/08/introducing-pytorch-for-fastai/)
  - write up, calling out the different course intents and advantages of dynamic execution

[Airbnb: Architecting a machine learning system for risk](https://medium.com/airbnb-engineering/architecting-a-machine-learning-system-for-risk-941abbba5a60)

### Data Analysis

[Big data meets Big Brother as China starts rating its citizens](http://www.wired.co.uk/article/chinese-government-social-credit-score-privacy-invasion)

[Airbnb: Data infrastructure at Airbnb](https://medium.com/airbnb-engineering/data-infrastructure-at-airbnb-8adfb34f169c)

[Airbnb: Knowledge repo, scaling knowledge](https://medium.com/airbnb-engineering/scaling-knowledge-at-airbnb-875d73eff091)

[Uber: Data Science Workbench](https://eng.uber.com/dsw/)

### Software Engineering

[Druid: Powering interactive data applications at Scale (video)](https://www.youtube.com/watch?v=vbH8E0nH2Nw)

### Visualisations

[Airbnb: Superset, scaling data access and visual insights](https://medium.com/airbnb-engineering/superset-scaling-data-access-and-visual-insights-at-airbnb-3ce3e9b88a7f)

[How Superset and Druid power real time analytics at Airbnb (video)](https://www.youtube.com/watch?v=W_Sp4jo1ACg)

- [Superset: an open source data exploration platform (video)](https://www.youtube.com/watch?v=NC9ehDUUu2o)
  - really nice product walkthrough by its creator

[Superset: source code on Github](https://github.com/apache/incubator-superset)

### Data Science

#### Ethics

- [FastAI: When data science destabilises democracy and facilitates genocide](http://www.fast.ai/2017/11/02/ethics/)
  - Fantastic write up providing numerous examples where unthinkingly optimising a metric has tangible real world implications.

*Unethical algorithms used to determine sentencing*

[Algorithm used in US courtrooms to determine likelihood of reoffending](https://www.youtube.com/watch?list=PLB2SCq-tZtVmadnKpO8WwKiFKteY5rHPT&time_continue=1624&v=WjKdKvDS10g) uses data about whether a persons parents separated and if their father had ever been arrested. **This means that people's prison sentences were longer or shorter depending on things their parents had done**.

*Feedback loops*

Meetup showed an example of men expressing more interest than women in tech meetups. As such, [Meetups algorithm recommended fewer tech meetups to women](https://www.youtube.com/watch?v=MqoRzNhrTnQ), with a result that fewer women would find out about and attend tech meetups, which could cause the algorithm to suggest even fewer tech meetups to women, and so on in a self-reinforcing feedback loop.

Another example is a [predictive policing algorithm](https://arxiv.org/abs/1706.09847) that predicts more crime in certain neighborhoods, causing more police officers to be sent to those neighborhoods, which can result in more crime being recorded in those neighborhoods, and so on.