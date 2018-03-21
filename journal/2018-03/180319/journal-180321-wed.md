# Wed 21 Mar 2018

## Example of using pipes in R

```r
library(validate)
cf <- check_that(women, height > 0, weight > 0, height/weight > 0.5)
summary(cf)
```

is the same as

```r
women %>% check_that(height > 0, weight > 0, height/weight > 0.5) %>% summary()
```

## Custom learning track with DataCamp

- Introduction to Data
    - learn study types, sampling strategies and experimental design

- Communicating with Data in the Tidyverse
    - create publication quality graphics and custom styled reports

- Foundations of inference
    - how to draw conclusions about a population from a sample of data with statistical inference

- Inference for numerical data
    - perform statistical inference on numerical data

- Manipulating time series data in R: Case Studies
    - follow on from 'Manipulating Time Series in R' using real case study data

- Visualising Time Series Data in R
    - use a stock picking case study to visualise time series

- Intermediate Portfolio Analysis in R
    - backtest, analyse, and optimise financial portfolios

- Reporting with R Markdown

- Data visualisation with ggplot2

- Building web applications in R with Shiny

- Building dashboards with shinydashboard


## Links

- RStudio
    - [RStudio cheat sheets](https://www.rstudio.com/resources/cheatsheets/)
    - [Official RStudio Docker images](https://hub.docker.com/r/rocker/rstudio/)

- [FiveThirtyEight: Forecasting Basketball players career performance](https://fivethirtyeight.com/features/how-were-predicting-nba-player-career/)

- [Wikipedia: Time series fan chart: visualising uncertainty in symmetric and non-symmetric forecasts](https://en.wikipedia.org/wiki/Fan_chart_(time_series))

- [Time series breakdout detection in R](https://flowingdata.com/2014/10/29/breakout-detection-in-r/)

- [Bivariate area charts in R](https://flowingdata.com/2015/10/01/bivariate-area-charts-in-r/)

- [PythonGraphGallery: Matploblib colours](https://python-graph-gallery.com/196-select-one-color-with-matplotlib/)
    - [Matplotlib colour maps](https://matplotlib.org/1.2.1/mpl_examples/pylab_examples/show_colormaps.hires.png)

- [Plotting different colour lines in Matplotlib](https://stackoverflow.com/questions/4805048/how-to-get-different-colored-lines-for-different-plots-in-a-single-figure)

- [Basic guide to running RStudio inside a Docker container](https://www.andrewheiss.com/blog/2017/04/27/super-basic-practical-guide-to-docker-and-rstudio/)

- [Writing multiple Pandas DataFrames to Excel worksheets](http://xlsxwriter.readthedocs.io/example_pandas_multiple.html)

- LaTeX
    - [Page layout in LaTeX](https://en.wikibooks.org/wiki/LaTeX/Page_Layout)
    - [Getting to grips with LaTeX](http://www.andy-roberts.net/writing/latex)

- [Hand curated, high quality resources for doing Data Journalism with R](https://rddj.info/)

- [Github repo with exploratory analysis and RMarkdown scripts to produce a data journalism piece]https://github.com/wpinvestigative/kushner_eb5_census)

- [Creating a reproducible R workflow](https://timogrossenbacher.ch/2017/07/a-truly-reproducible-r-workflow/)
    - [Template for creating reproducible RMarkdown documents for data journalism](https://github.com/grssnbchr/rddj-template)

- [Writing reproducible reports in R with markdown, knitr and pandoc](https://nicercode.github.io/guides/reports/)

- [Working with databases in R](https://datascienceplus.com/working-with-databases-in-r/)

- [BigQuery data processing workflow for R](http://zevross.com/blog/2015/01/13/a-new-data-processing-workflow-for-r-dplyr-magrittr-tidyr-ggplot2/)

- [validate R package: easy data validation](https://github.com/data-cleaning/validate)
    - allows you to write validation rules based on domain knowledge
    - results can be summarised and plotted

- [Matplotlib: Plot object](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.plot.html#matplotlib.pyplot.plot)

- [Jake VanderPlas: Visualisation with Seaborn](https://jakevdp.github.io/PythonDataScienceHandbook/04.14-visualization-with-seaborn.html)

- [Jake VanderPlas: Working with Time Series in Pandas](https://jakevdp.github.io/PythonDataScienceHandbook/03.11-working-with-time-series.html)