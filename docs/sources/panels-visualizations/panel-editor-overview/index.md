---
aliases:
  - ../dashboards/add-organize-panels/
  - ../dashboards/dashboard-create/
  - ../panels/add-panels-dynamically/about-repeating-panels-rows/
  - ../panels/add-panels-dynamically/configure-repeating-panels/
  - ../panels/add-panels-dynamically/configure-repeating-rows/
  - ../panels/working-with-panels/
  - ../panels/working-with-panels/add-panel/
  - ../panels/working-with-panels/navigate-inspector-panel/
  - ../panels/working-with-panels/navigate-panel-editor/
  - add-organize-panels/
keywords:
  - panel
  - dashboard
  - dynamic
  - add
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Panel editor
title: Panel editor
description: Learn about the features of the panel editor
weight: 20
refs:
  transform-data:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/transform-data/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/transform-data/
  the-overview-of-grafana-alerting:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/
  table:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/table/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/table/
  add-a-query:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/#add-a-query
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/#add-a-query
  saved-queries:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/#saved-queries
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/#saved-queries
  save-query:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/#save-a-query
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/#save-a-query
---

# Panel editor

* goal
  * Grafana panel editor's areas

* == | edit a panel
* allows
  * modify ALL visualization's elements (data source, queries, time range, and visualization display options)

![Panel editor](/grafana/media/docs/panels-visualizations/panel-editor.png)

## Panel header

* display
  * dashboard | panel appears

* ALLOWED controls
  - **Back to dashboard**
    - Return to the dashboard / changes
      - applied
      - NOT YET saved
  - **Discard panel changes**
    - discard changes / you have made -- since -- your last saved the dashboard
  - **Save dashboard**
    - Save your changes to the dashboard

![Panel editor](/grafana/media/docs/panels-visualizations/panel-editor-header.png)

## Visualization preview

- **Table view** 
  - visualization is converted -- to a -- table
    - == raw data
      - == ❌NOT include transformations or formatting options❌
  - uses
    - troubleshooting
- **Time range controls** 
  - by default,
    - browser local timezone OR timezone selected | higher level
- **Refresh** 
  - Query the data source

![Panel editor](/grafana/media/docs/panels-visualizations/panel-editor-visualizationPreview.png)

## Data section

- **Queries**
  - Select your data source
  - [Add queries](ref:add-a-query)
- **Transformations** 
  - [Transform data](ref:transform-data)
- **Alert**
  - [the overview of Grafana Alerting](ref:the-overview-of-grafana-alerting)

![Panel editor](/grafana/media/docs/panels-visualizations/panel-editor-dataSection.png)

## Panel display options

* allows
  * configuring ALL your data visualization's aspect 

![Panel editor](/grafana/media/docs/panels-visualizations/panel-editor-displayOptions.png)
