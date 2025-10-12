---
title: Value mappings options
comments: |
  This file is used in the following visualizations: bar chart, bar gauge, candlestick, canvas, gauge, geomap, histogram, pie chart, stat, state timeline, status history, table, time series, trend
---

* Value mapping
  * == technique /
    * allows
      * changing how data appears | visualization AXIS Y

* options
  - **Condition** - Choose what's mapped to the display text and (optionally) color:
    - **Value**
      - == SPECIFIC values
    - **Range** 
      - Numerical ranges
    - **Regex**
      - Regular expressions
    - **Special**
      - _Examples:_ `Null`, `NaN` (not a number), or boolean values like `true` and `false`
  - **Display text**
  - **Color**
    - OPTIONAL
  - **Icon**
    - Canvas ONLY

* see [Configure value mappings](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-value-mappings/)
