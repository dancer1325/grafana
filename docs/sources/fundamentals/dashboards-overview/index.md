---
description: Learn how Grafana dashboards are built.
keywords:
  - grafana
  - dashboards
  - panel
  - data source
  - transform
  - query
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Dashboard overview
title: Grafana dashboards overview
weight: 390
refs:
  transform-data:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/transform-data/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/transform-data/
---

# Grafana dashboards overview

* dashboard
  * == panelS / display data | beautiful visualizations (graphs, charts, ...) 
    * gates | pass data
      * plugin, 
      * query,
      * OPTIONAL transformation 

      ![](/grafana/media/docs/dashboards-overview/dashboard-component-architecture.png)

  * steps to determine the dashboard
    * dashboard requirements
    * data sources  
    * plugin
    * query
    * transformation
    * visualization
  * help us 
    * comprehend & manage systems
  * uses 
    * | observability world
    
    ![](/grafana/media/docs/dashboards-overview/complex-dashboard-example.png)

## Data sources

* data source
  * == entity / consists of data
    * _Example:_ SQL database, Grafana Loki, Grafana Mimir, or a JSON-based API
    * == basic CSV
  * / EACH data source, DIFFERENT
    * structure
    * query methods

## Plugins

* Grafana plugin
  * == software / adds NEW capabilities | Grafana
    * MOST COMMON ones ALREADY pre-installed
  * types
    * _data source plugins_
      * allows
        * take your desired query
        * retrieve data -- from the -- data source,
          * ALLOWED formats (JSON, rows and columns, or CSV) 
        * transform the data -- to the -- Grafana dashboard,
        * reconcile the differences BETWEEN data source's data model vs Grafana dashboards' data model ([data frame](https://grafana.com/developers/plugin-tools/key-concepts/data-frames))

## Queries

* Queries
  * == foundation of every visualization in Grafana 
  * allow you to
    * reduce your data -- to a -- specific dataset
  * uses
    * comprehend your system & operational processes

* query language
  * -- depend on -- data source 
  * | Grafana dashboard,
    * MULTIPLE can be used

## Transformations

* [transformation](ref:transform-data)
  * == manipulation of data / returned by a query
    * | refresh the dashboard, 
      * transformation applies -- to the -- data source's latest data  
  * use cases
    * ❌data format | visualization does NOT meet your requirements❌
      * _Examples:_
        - combine 2 fields together
        - | CSV data, convert a field type
        - filter, join, merge, or perform other SQL-like operations / might NOT be supported -- by the -- underlying data source or query language
  * located | panel's Transform tab

![](/grafana/media/docs/dashboards-overview/example-transform-chain.png)

## Panels

* panel
  * == journey to a Grafana visualization's final gate 
  * == container /
    * displays the visualization
    * query data
  * 's configuration
    * place | specify how to see the data
      * type of visualization
      * panel's options
