# Thu 23 Nov 2017

## Investment data product

### Features

- Add summary features that calculate with transaction charge what the share price would have to be to break even if stock held over period X (e.g. 4 weeks, 6 months, 1 year). Similar to RET28 at work?

- Then use regression and a moving average to predict how long it will take to reach that price with todays share price, as a measure of minimum hold
  - update daily?

- Daily predict stock movement direction (not magnitude), i.e. up/down
  - retain each days predictions and match against actual observed outcome
  - use past X as an alerting metric, e.g. 4 downs in a row flag a warning
  - when warning flagged run regression to predict how long until stock reaches loss price (below the price + transaction fee)

### Ideas

- Use XPS13 left on permanently as scraping server. Can dump raw html scrape archive to hard disk then compress and back up somewhere in case we need to go back and get additional data.

- Parse html for relevant figures, then export daily data
  - add to DataFrame and save to csv?
  - export as JSON object

- Stream data into Druid datastore

## Links

### Machine Learning

- [ArXiv: AOGNets: Deep AND-OR grammar networks for visual recognition](https://arxiv.org/pdf/1711.05847.pdf)
  - very competitive technique on ImageNet and CIFAR

#### Capsule Networks

- [Geoffey Hinton: What is wrong with convolutional neural nets (video)](https://www.youtube.com/watch?v=rTawFwUvnLE)
  - long but good talk on the theory behind capsule networks

### Data Analysis

[Measuring User Engagement by Mounia Lalmas (pdf book)](http://www.dcs.gla.ac.uk/~mounia/Papers/MUE.pdf)

### Data Science

[Misunderstandings between business leaders and data scientists](https://medium.com/@anandr42/the-data-science-delusion-7759f4eaac8e)

### Software Engineering

[Ingesting csv files into Druid](http://neontapir.github.io/professional/2017/02/10/ingest-csv-druid/)