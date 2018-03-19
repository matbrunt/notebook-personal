# Mon 26 Feb 2018

## Analysis template structure

- build image
    - copy in helper scripts to image filesystem
    - on changes to cookiecut build a new image (tag with 'latest' and version string from changelog)

- CHANGELOG.md
    - every time update helper scripts add a new version string in here with summary
    - this means helpers scripts are cookiecut to each new instance on creation, and Docker image updated with changes as well
    - copy changelog into Docker image working directory root, so can tell what version things are

- workbooks (Tableau)

- notebooks (Jupyter)

- app (helper code, ETL pipeline)

- reports (where we save the story for presentation to others)
    - output pdfs here
    - source markdown to generate pdfs here (put images in ./figures sub-directory)
    - can generate graphics in notebook folder, copy to ./figures and clean figures version up in graphics package

## Links

- [Forecasting with daily data](https://robjhyndman.com/hyndsight/dailydata/)

- [Seasonal ARIMA models (fpp book)](https://www.otexts.org/fpp/8/9)

- [Calculating Compound Annual Growth Rates (CAGR) in Python](https://feliperego.github.io/blog/2016/08/10/CAGR-Function-In-Python)
    - CAGR measures the mean growth rates of money or units / quantities of something over the years

- [Time series analysis with Pandas](http://earthpy.org/pandas-basics.html)