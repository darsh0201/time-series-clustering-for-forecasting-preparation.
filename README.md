## Time Series Clustering For Forecasting Preparation

The M5 dataset is a set of time series of daily sales by item Categories, Departments, Stores, and Items. These levels of granularity have a heirarchical structure, in that: 
- A `Category` has multiple `Departments`
- A `Department` spans across multiple `Stores`
- A `Department` contains multiple `Items`
- A combination of `Item` and `Store` is a the most granular level of series (SKU). 

Unlike more vanilla time series forecasting tasks - where one uses a single series to predict the future of the series, this structure allows for transfer learning between series. 

For example: It may be that a group of items have similar sales patterns, due to seasonality in demand or supply, etc. Thus, it would make sense for a model to learn learn shared patterns to provide more robust forecasts. 

On the other hand, demand for groups of items might differ substancially due to external forces. Training a model to try and find similarities between these groups might only introduce noise - as the demand/supply for these items are structurally different.

### Clustering series

The purpose of this notebook is to demonstrate how we might group items that have similar underlying structure before diving into modeling using several clustering approaches. This way, we could pre-process series within groups in a similar way, and train a model for each cluster which specializes in learning this underlying structure. 

In this notebook I'll use a naive heirarchical method to cluster the series, point out the shortcoming of this approach, and speak about a method to approach these shortcomings called Dynamic Time Warping.
