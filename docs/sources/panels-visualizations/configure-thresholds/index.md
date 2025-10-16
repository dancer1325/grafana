---
aliases:
  - ../panels/
  - ../panels/configure-thresholds/
  - ../panels/specify-thresholds/about-thresholds/
  - ../panels/specify-thresholds/add-a-threshold/
  - ../panels/specify-thresholds/add-threshold-to-graph/
  - ../panels/specify-thresholds/delete-a-threshold/
  - ../panels/thresholds/
description: Configure thresholds in your visualizations
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Configure thresholds
title: Configure thresholds
weight: 100
refs:
  table:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/table/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/table/
  histogram:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/histogram/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/histogram/
  bar-chart:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/bar-chart/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/bar-chart/
  time-series:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/time-series/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/time-series/
  trend:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/trend/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/trend/
  geomap:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/geomap/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/geomap/
  stat:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/stat/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/stat/
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
---

# Configure thresholds

* threshold
  * == metric's value OR limit /
    * | met OR exceeded,
      * reflected VISUALLY
  * uses
    * style & color your visualizations -- based on -- query results
  * use cases
    * | time series visualization
      * color grid lines & regions
    * | stat,
      * color the background OR value text
    * | state timeline,
      * define regions & region colors
    * | gauge
      * color the gauge & threshold markers
    * | geomap
      * color markers
    * | table,
      * color cell text or background 

* _Example:_ [here](https://play.grafana.org/d/000000167/)

## Supported visualizations

- [Bar chart](ref:bar-chart)
- [Bar gauge](ref:bar-gauge)
- [Candlestick](ref:candlestick)
- [Canvas](ref:canvas)
- [Gauge](ref:gauge)
- [Geomap](ref:geomap)
- [Histogram](ref:histogram)
- [Stat](ref:stat)
- [State timeline](ref:state-timeline)
- [Status history](ref:status-history)
- [Table](ref:table)
- [Time series](ref:time-series)
- [Trend](ref:trend)

## Thresholds options

### Threshold value

* == MINIMUM value / triggers the threshold + related-color

### Thresholds mode

- **Absolute**
  - == thresholds / defined by a number
- **Percentage**
  - thresholds / defined -- relative to -- minimum or maximum

### Show thresholds

* ALLOWED |
  * bar chart,
  * candlestick,
  * time series,
  * trend visualizations

* goal
  * if
  * how to show thresholds

| Option                               | Example                                                                                                                                                                                              |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Off                                  |                                                                                                                                                                                                      |
| As lines                             | {{< figure max-width="500px" src="/media/docs/grafana/panels-visualizations/screenshot-thresholds-lines-v10.4.png" alt="Visualization with threshold as a line" >}}                                  |
| As lines (dashed)                    | {{< figure max-width="500px" src="/media/docs/grafana/panels-visualizations/screenshot-thresholds-dashed-lines-v10.4.png" alt="Visualization with threshold as a dashed line" >}}                    |
| As filled regions                    | {{< figure max-width="500px" src="/media/docs/grafana/panels-visualizations/screenshot-thresholds-regions-v10.4.png" alt="Visualization with threshold as a region" >}}                              |
| As filled regions and lines          | {{< figure max-width="500px" src="/media/docs/grafana/panels-visualizations/screenshot-thresholds-lines-regions-v10.4.png" alt="Visualization with threshold as a region and line" >}}               |
| As filled regions and lines (dashed) | {{< figure max-width="500px" src="/media/docs/grafana/panels-visualizations/screenshot-thresholds-dashed-lines-regions-v10.4.png" alt="Visualization with threshold as a region and dashed line" >}} |
