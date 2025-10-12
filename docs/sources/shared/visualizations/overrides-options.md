---
title: Field overrides options
comments: |
  This file is used in the following visualizations: bar chart, bar gauge, candlestick, canvas, gauge, geomap, heatmap, histogram, pie chart, stat, state timeline, status history, table, time series, trend, xy chart
---

* allow you
  * customize visualization settings / specific fields or series

* ALLOWED override options

| Option                         | Description                                                                                                            |
| ------------------------------ |------------------------------------------------------------------------------------------------------------------------|
| Fields with name               | Select a field -- from the -- available fields                                                                         |
| Field with name matching regex | Specify fields to override -- with a -- regular expression                                                             |
| Fields with type               | Select fields by type (_Examples:_ string, numeric, or time)                                                           |
| Fields returned by query       | Select all fields returned -- by a -- specific query (_Examples:_ A, B, or C)                                          |
| Fields with values             | Select all fields returned - by -- your defined reducer condition (_Examples:_ **Min**, **Max**, **Count**, **Total**) |

* see [Configure field overrides](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-overrides/)
