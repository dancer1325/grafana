---
aliases:
  - ../panels/configure-overrides/
  - ../panels/field-overrides/
  - ../panels/override-field-values/
  - ../panels/override-field-values/about-field-overrides/
  - ../panels/override-field-values/add-a-field-override/
  - ../panels/override-field-values/delete-a-field-override/
  - ../panels/override-field-values/edit-field-override/
  - ../panels/override-field-values/view-field-override/
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Configure field overrides
title: Configure field overrides
description: Configure field overrides to customize visualization settings
weight: 110
refs:
  state-timeline:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/state-timeline/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/state-timeline/
  gauge:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/gauge/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/gauge/
  bar-gauge:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/bar-gauge/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/bar-gauge/
  canvas:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/canvas/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/canvas/
  candlestick:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/candlestick/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/candlestick/
  status-history:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/status-history/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/status-history/
  heatmap:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/heatmap/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/heatmap/
  rename-by-regex-transformation:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/transform-data/#rename-by-regex
    - pattern: /docs/grafana-cloud
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/transform-data/#rename-by-regex
  histogram:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/histogram/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/histogram/
  table:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/table/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/table/
  bar-chart:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/bar-chart/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/bar-chart/
  pie-chart:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/pie-chart/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/pie-chart/
  time-series:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/time-series/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/time-series/
  geomap:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/geomap/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/geomap/
  xy-chart:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/xy-chart/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/xy-chart/
  trend:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/trend/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/trend/
  stat:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/stat/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/stat/
---

# Configure field overrides

* allow you to
  * customize visualization settings / specific fields or series

## Supported visualizations

- [Bar chart](ref:bar-chart)
- [Bar gauge](ref:bar-gauge)
- [Candlestick](ref:candlestick)
- [Canvas](ref:canvas)
- [Gauge](ref:gauge)
- [Geomap](ref:geomap)
- [Heatmap](ref:heatmap)
- [Histogram](ref:histogram)
- [Pie chart](ref:pie-chart)
- [Stat](ref:stat)
- [State timeline](ref:state-timeline)
- [Status history](ref:status-history)
- [Table](ref:table)
- [Time series](ref:time-series)
- [Trend](ref:trend)
- [XY chart](ref:xy-chart)

## Override rules

### Fields with name

* -- based on --- name

### Fields with name matching regex

* -- based on -- ALL fields / match a regular expression
* ❌NOT rename the field❌

### Fields with type

* -- based on -- ALL fields / match the type

### Fields returned by query

* -- based on -- specific query

### Fields with values

* -- based on -- defined reducer condition
