---
aliases:
  - ../../features/panels/singlestat/
  - ../../features/panels/stat/
  - ../../panels/visualizations/stat-panel/
  - ../../reference/singlestat/
  - ../../visualizations/stat-panel/
description: Configure options for Grafana's stat visualization
keywords:
  - grafana
  - docs
  - stat panel
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Stat
weight: 100
refs:
  calculation-types:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/calculation-types/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/calculation-types/
  create-dashboard:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/build-dashboards/create-dashboard/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/dashboards/build-dashboards/create-dashboard/
---

# Stat

* replacement of Singlestat visualization
  * Reason:🧠
    * | Grafana 7.0, 
      * deprecated
    * | Grafana 8.0
      * removed 

* stat
  * display 1! value of interest /
    * | background, optional graph sparkline
      * such as the latest or current value of a series

* graph sparkline
  * ONLY AVAILABLE | stat visualizations
  * == small time-series graph / displayed | background

* uses
  * monitor key metrics | glance
  * 1! value of interest 
    * _Examples:_ total number of sales, number of high priority bugs, number of deployments, ...
  * aggregated data | 1! value
    * _Example:_ your services' average response time
  * highlight values ABOVE your normal thresholds

* _Example:_ [Grafana playground](https://play.grafana.org/d/Zb3f4veGk/)

## Configure a stat visualization

* [Youtube video](https://www.youtube.com/watch?v=yNRnLyVntUw&t=1048s) 
* [how to easily retrieve values from a range in Grafana using a stat visualization](https://grafana.com/blog/2023/10/18/how-to-easily-retrieve-values-from-a-range-in-grafana-using-a-stat-panel/)

## Supported data formats
- **Single values** 
  - _Example:_ numerical, strings, or boolean values.
- **Time-series data**
  - [Calculation types](ref:calculation-types) can be applied to your time-series data to display single values over a specified time range.

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


### Stat styles

* way to adjust the layout

<!-- prettier-ignore-start -->
| Option                        | Description                                                                                                                                                                                                                                                                                                                                                                                                     |
|-------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Orientation                   | == orientation values direction <br/> <ul><li>**Auto** <br/> &nbsp;&nbsp; Grafana selects AUTOMATICALLY the ideal orientation </li><li>**Horizontal** <br/> &nbsp;&nbsp; Bars stretch horizontally, left to right.</li> <li>**Vertical** <br/> &nbsp;&nbsp; Bars stretch vertically, top to bottom.</li></ul>                                                                                                   |
| [Text mode](#text-mode)       |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [Wide layout](#wide-layout)   |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Color mode                    | Select a color mode. Choose from: <ul><li>**None** - No color applied to the value.</li><li>**Value** - Applies color to the value and graph area.</li><li>**Background Gradient** - Applies color to the value, graph area, and background, with a slight background gradient.</li><li>**Background Solid** - Applies color to the value, graph area, and background, with a solid background color.</li></ul> |
| Graph mode                    | graph sparkline mode <br/> <ul><li>**None** <br/> &nbsp;&nbsp; hides the graph sparkline == ONLY the value </li><li>**Area** <br/> &nbsp;&nbsp; graph sparkline BELOW the value <br/> &nbsp;&nbsp; This requires that your query returns a time column.</li></ul> if the panel becomes too small -> AUTOMATICALLY hide the graph sparkline                                                                      |
| Text alignment                | Select an alignment mode. Choose from: <ul><li>**Auto** - If only a single value is shown (no repeat), then the value is centered. If multiple series or rows are shown, then the value is left-aligned.</li><li>**Center** - Stat value is centered.</li></ul>                                                                                                                                                 |
| Show percent change           | percent change <br/> Disabled by default <br/> requirements: **Value options** > **Show** == **Calculate**                                                                                                                                                                                                                                                                                                      |
| Percent change color mode     | requirements: **Show percent change** == enabled <br/> <ul><li>**Standard** - Green if the percent change is positive, red if the percent change is negative.</li><li>**Inverted** - Red if the percent change is positive, green if the percent change is negative.</li><li>**Same as Value** - Use the same color as the value.</li></ul>                                                             |
<!-- prettier-ignore-end -->

#### Text mode

- **Auto**
  - if there are MULTIPLE series OR fields -> value and name
- **Value**
  - ONLY value
  - | hover tooltip,
    - name is displayed
- **Value and name**
  - BOTH
- **Name**
  - show name
  - | hover tooltip,
    - value is displayed 
  - use cases
    - ONLY important name & color
- **None**
  - EMPTY
  - | hover tooltip,
    - name & value are displayed

#### Wide layout

* requirements
  * text mode == value and name

* ALLOWED values
  - **On**
    - Wide layout is enabled
      - -> if the panel is wide enough -> value & name are displayed side-by-side / value | right 
    - default one
  - **Off** 
    - Wide layout is disabled
      - -> value ALWAYS underneath the name

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
