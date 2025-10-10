---
aliases:
  - ../panels/query-a-data-source/download-raw-query-results/
  - ../panels/query-a-data-source/inspect-query-performance/
  - ../panels/query-a-data-source/inspect-request-and-response-data/
  - ../panels/working-with-panels/navigate-inspector-panel/
labels:
  products:
    - cloud
    - enterprise
    - oss
title: The panel inspect view
description: Inspect the raw data of your panels to understand and troubleshoot them
weight: 30
---

# The panel inspect view

* panel inspect view
  * steps
    * Dashboard > choose 1 > panel menu > inspect
  * uses, about your panels
    * understand 
    * troubleshoot
  * allows
    * inspect the Grafana panel's raw data
    * export -- via -- (CSV) file
  * options
    2. **Data tab -**
       1. raw data / returned by the query + transformations applied
    3. **Stats tab** 
       1. == statistics
          1. how long your query takes
          2. how many queries / it returns
    4. **JSON tab -**
       1. allows you to
          1. view & copy
    5. **Query tab -**
       1. | Grafana queries the data source,
          1. shows the requests to the server 
       2. uses
          1. troubleshoot a query / returns unexpected results 
    6. **Error tab -**
       1. requirements
          1. query returns error
       2. Shows the error 

![](/grafana/media/docs/panels-visualizations/panelInspector.png)

## Download raw query results

* options
  * data BEFORE OR AFTER the panel applies field options OR field option overrides

* steps
  * panel menu > inspect > **Data**
    * if your panel contains multiple queries or queries multiple nodes -> choose data frame
      - choose 1 data frame
      - **Join by time**
        - ALL your queries / column
    1. if you want
       1. data BEFORE applying field overrides -> **Formatted data** toggle
       2. CSV file / formatted for Excel -> **Download for Excel**
    1. **Download CSV**

## Inspect query request and response data

* steps
  * panel menu > inspect > **Query** > Refresh
