# Wed 22 Nov 2017

### D3 ideas

- [Flight animation with D3.js](http://www.tnoda.com/blog/2014-04-02)

- ![Journey path reveals on hover over](http://eng.uber.com/wp-content/uploads/2016/05/blog_arcs.gif)
    - use this to visualise routes from airports, drawn over a regional (Europe) or global map

### Druid

Funnel analysis in Druid, plugin architecture, how?

Raw csv files
Ingestion script to load csv into Druid and persist to volume, so can set up from fresh check out
- streaming ingestion? Then can use the same technique to add daily data in when system live

Immutable segment for base data, OHLC etc that won't change once written. Means its read optimised.

Batch vs Streaming ingestion

[Druid cluster Dockerfile](https://hub.docker.com/r/druidio/example-cluster/~/dockerfile/)

[Druid homespage](http://imply.io/docs/latest/quickstart)

## Links

## Data Analysis

[Uber: The purpose of platforms in data science](https://medium.com/@novakkm/the-purpose-of-platforms-in-data-science-965e2124edf8)

[Uber: Data Science Workbench](https://eng.uber.com/dsw/)

### Visualisations

[Visualising Vancouvers property value data](http://uber.github.io/deck.gl/#/examples/core-layers/geojson-layer)

[Druid: powering interactive data applications at scale (video)](https://www.youtube.com/watch?v=vbH8E0nH2Nw)

[Building an open source streaming analytics stack with Kafka and Druid](https://www.youtube.com/watch?v=5nVEWee9fc4)

[Open Sourcing deck.gl 4.0: Uber Engineering’s Framework for Advanced Data Visualization](https://eng.uber.com/deck-gl-4-0/)

[Uber: Engineering intelligence through data visualisation](https://eng.uber.com/data-viz-intel/)

[luma.gl - WebGL 2.0 framework using ES6 for a component based platform](https://github.com/uber/luma.gl)