---
title: "Incremental Refresh in Power BI"
---

<LineBreak lines=1/>

![Power BI Incremental Refresh](/pbi-incremental-refresh.png)

## What is incremental refresh in Power BI?
Behind every Power BI dataset is a SQL Server Analysis Services (SSAS) tabular data model. This underlying technology has built-in partition support for larger datasets. Partitions divide tables into logical parts, which can then be refreshed independently. 

Incremental refresh brings that same partition support to the forefront in Power BI, enabling business users and IT professionals to refresh sections of a dataset.


## Why would you use incremental refresh in Power BI?
The TL;DR version:

- Instead of reloading entire data model, only new data is loaded
- Dataset failures can and do happen
- Reduce load on Power BI
- Reduce load on source systems
- Allows for near real-time data

**The fine print:**

If you're creating Power BI datasets for enterprise scenarios, you're likely dealing with quite a lot of data. Datasets between 10 million and 500 million rows are not uncommon, and for the most part Power BI can handle models of this size (provided you have the appropriate licensing and data modeling best practices in place).

Power BI's default behaviour is to reload the entire data model (and every row of each table) every time a refresh is initiated. It turns out that moving all this data from your data warehouse/source systems, applying data transformations, and loading it into Power BI takes a good deal of time and computing resources.

When you set up incremental refresh, Power BI only needs to load new data instead of starting from scratch each refresh. This means your dataset refresh will take much less time. There are also some other, less obvious advantages.

The first less obvious advantage to using incremental refresh is that you reduce the overall load on Power BI. Because of the reduction in data being loaded, enabling incremental refresh means more computing resources will be available for Power BI to render visualizations, refresh other datasets, or run queries against your data models. 

Secondly, you reduce load on source systems. Refreshing large Power BI datasets puts stress on your data warehouse or other data sources as they must move (and possibly transform) large data volumes. 

Dataset refresh failures happen more often than you'd think, and are often attributed to query timeouts from data sources. By reducing the amount of data required to refresh your Power BI model, your refreshes will be more reliable and more resources will be saved for your data warehouse to run other queries. 

The last less obvious benefit of implementing incremental refresh in Power BI is that it can help enable **near real-time data**. 

Because refreshes take less time to complete, you can decrease the time between each refresh. With Power BI Premium you can schedule up to 48 refreshes per day, so your reports and dashboards can show insights that are truly up-to-date. 

_*Note: if you'd like to enable **truly real-time data**, you should look into streaming datasets in Power BI._

## Why wouldn't you use incremental refresh in Power BI?
For smaller datasets under 50 mb with few data transformations, I actually wouldn't recommend setting up incremental refresh. 

Datasets of this size won't benefit as much as larger datasets - their refresh times are relatively short and the loads they place on Power BI are less expensive. 

There is additional administrative overhead required in setting up and maintaining the incremental refresh policies, which likely outweigh the performance benefit you may realize.

## How to enable incremental refresh in Power BI
Incremental refresh is currently available for Premium and Pro licencing in Power BI. 

The Microsoft documentation comprehensively outlines the steps required for setup, so I won't reinvent the wheel here. 

You can check out the step-by-step instructions here: https://docs.microsoft.com/en-us/power-bi/admin/service-premium-incremental-refresh