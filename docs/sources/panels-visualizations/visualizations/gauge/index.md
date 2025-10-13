---
aliases:
  - ../../features/panels/gauge/
  - ../../panels/visualizations/gauge-panel/
  - ../../visualizations/gauge-panel/
description: Configure options for Grafana's gauge visualization
keywords:
  - grafana
  - gauge
  - gauge panel
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Gauge
weight: 100
refs:
  calculation-types:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/calculation-types/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/calculation-types/
---

# Gauge

* Gauges
  * == 1!-value visualizations
  * allow you
    * quickly visualize CURRENT value | min and max range

* uses
  * track
    - CPU consumption (0-100%)
    - RAM availability
    - Service level objectives (SLOs)

## Configure a gauge visualization

* [youtube](https://www.youtube.com/watch?v=QwXj3y_YpnE)
* _Example:_ [Grafana playground](https://play.grafana.org/d/KIhkVD6Gk/)

## Supported data formats

* requirements
  * dataset / has >=1 numeric field

### 1! value

| GaugeName | GaugeValue |
| --------- | ---------- |
| MyGauge   | 5          |


* display
  * 1! empty gauge

* ALTHOUGH you ONLY have 1 value & want to define a minimum and maximum -> set them manually | [Standard options](#standard-options)

### 1 row / MULTIPLE values


| Identifier | value1 | value2 | value3 |
| ---------- | ------ | ------ | ------ |
| Gauges     | 5      | 3      | 10     |

* display
  * MULTIPLE gauges

* minimum & maximum
  * are defined AUTOMATICALLY
  * set the internal shadow -- as a -- percentage

### Example - Multiple rows & values

| Identifier | value1 | value2 | value3 |
| ---------- | ------ | ------ | ------ |
| Gauges     | 5      | 3      | 10     |
| Indicators | 6      | 9      | 15     |
| Defaults   | 1      | 4      | 8      |

* display ALL values / MULTIPLE data sets

## Configuration options

{{< docs/shared lookup="visualizations/config-options-intro.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Panel options

{{< docs/shared lookup="visualizations/panel-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Value options

* uses
  * refine how your visualization displays its values

<!-- prettier-ignore-start -->
| Option      | Description                                                                                                                                                                                         |
|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Show        | <ul><li>**Calculate** <br/> &nbsp;&nbsp; display 1! value -- based on -- ALL rows</li><li>**All values** <br/> &nbsp;&nbsp; display SEPARATE stat / EACH row                                        |
| Calculation | requirements: show == **Calculate** <br/> == reducer function / Grafana use to reduce MANY fields -- to -- 1! value <br/> [Calculation types](ref:calculation-types) |
| Limit       | requirements: show == **All values** <br/> == MAXIMUM number of rows / display                                                                                                                      |
| Fields      | field / display \| visualization  <br/>  &nbsp;&nbsp; -- depend on -- AVAILABLE fields                                                                                                              |

### Gauge options

* adjust the gauge

| Option                                            | Description                                                                                                                                                                                                                                                                                                   |
|---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Orientation                                       | == orientation values direction <br/> <ul><li>**Auto** <br/> &nbsp;&nbsp; Grafana selects AUTOMATICALLY the ideal orientation </li><li>**Horizontal** <br/> &nbsp;&nbsp; Bars stretch horizontally, left to right.</li> <li>**Vertical** <br/> &nbsp;&nbsp; Bars stretch vertically, top to bottom.</li></ul> |
| Show threshold labels                             | enable threshold values                                                                                                                                                                                                                                                                                       |
| [Show threshold markers](#show-threshold-markers) | threshold band is shown OUTTSIDE the inner gauge value band                                                                                                                                                                                                                                                   |
| Gauge size                                        | Choose a gauge size mode:<ul><li>**Auto** - Grafana determines the best gauge size.</li><li>**Manual** - Manually configure the gauge size.</li></ul>This option only applies when **Orientation** is set to **Horizontal** or **Vertical**.                                                                  |
| Min width                                         | Set the minimum width of vertically-oriented gauges. If you set a minimum width, the x-axis scrollbar is automatically displayed when there's a large amount of data. This option only applies when **Gauge size** is set to **Manual**.                                                                      |
| Min height                                        | Set the minimum height of horizontally-oriented gauges. If you set a minimum height, the y-axis scrollbar is automatically displayed when there's a large amount of data. This option only applies when **Gauge size** is set to **Manual**.                                                                  |
| Neutral                                           | set the starting value -- from which -- fill every gauge                                                                                                                                                                                                                                      |

### Text size

Adjust the sizes of the gauge text.

- **Title** - Enter a numeric value for the gauge title size.
- **Value** - Enter a numeric value for the gauge value size.

### Standard options

{{< docs/shared lookup="visualizations/standard-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Data links and actions

{{< docs/shared lookup="visualizations/datalink-options-1.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Value mappings

{{< docs/shared lookup="visualizations/value-mappings-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Thresholds

{{< docs/shared lookup="visualizations/thresholds-options-2.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Field overrides

{{< docs/shared lookup="visualizations/overrides-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}
