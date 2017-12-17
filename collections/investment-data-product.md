# Investment Data Product

## Components

### Scraper / Data Gathering

- Web scraper against Yahoo Finance pages.
    - store each page imprint to disk, zip if possible to reduce data size.
    - at the same time parse html for relevant stats and add to a DataFrame
        - save DataFrame to csv and overwrite data file after each parse
    - scrape from behind vpn tunnel to protect home IP
    - how often to run? Will fundamentals change between quarterly reports
    - can we tie in a data source for when the next company reports are due?

- can we use direct calls to Google Finance API instead of web scraping?

## Concepts

- Price/Book ratio < 0.7
    - this ratio is how much money will be left over for shareholders if the company goes bankrupt and sells all its assets to clear its liabilities

- Price Earnings/Growth over 5 years, < 1.0
    - perfect 1.0 represents a fair value
    - don't want something consistently less than 1.0
    - `0 < PEG5 < 1`
    - variable name `PEG5` as Price Earnings Growth ratio over 5 years

[PEG ratio](https://youtu.be/wu_nUppNQhw?list=PLQVvvaa0QuDejNczz7dbpyu3JnwUBvNch)

The PEG ratio of a company fairly priced is going to equal its growth rate.
Peter Lynch - One up on wall street

If PE is 10, but growth is 20%, this is a 0.5 PEG ratio.
Want less than 1.0, but exclude any negative PEG ratio (this happens if negative growth)

Compare PEGs between companies in same sector to find best company in that company.

Look for something with a low PE ratio
