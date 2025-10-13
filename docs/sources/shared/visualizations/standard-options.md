---
title: Standard options
comments: |
  This file is used in the following visualizations: bar chart, bar gauge, candlestick, canvas, gauge, geomap, histogram, pie chart, stat, state timeline, status history, table, time series, trend
---

* goal
  * how to display field data | your visualizations

* ⚠️apply | ALL fields or series⚠️
  * ⚠️if you want MORE granular control -> [Configure overrides](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-overrides/)⚠️

| Option        | Description                                                                                                          |
| ------------- |----------------------------------------------------------------------------------------------------------------------|
| Unit          | == axis Y' unit                                                                                                      |
| Min/Max       | if you leave EMPTY -> calculated AUTOMATICALLY <br/> == Y's minimum and maximum values                               |
| Field min/max | Grafana calculate the min or max of each field individually -- based on the -- minimum or maximum value of the field |
| Decimals      | if you leave EMPTY -> calculated AUTOMATICALLY <br/> == y's number of decimals                                       |
| Display name  | ALL fields displayed name <br/> if you want to make customizable -> use variables                                    |
| Color scheme  | ALLOWED single OR multiple colors                                                                                    |
| No value      | if the field value is empty OR null -> what to display <br/> by default, hyphen (-)                                  |

* see [Configure standard options](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-standard-options/)
