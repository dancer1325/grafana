---
aliases:
  - ../../panels/visualizations/bar-chart/
  - ../../visualizations/bar-chart/
description: Configure options for Grafana's bar chart visualization
keywords:
  - grafana
  - docs
  - bar chart
  - panel
  - barchart
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Bar chart
weight: 100
refs:
  standard-options-definitions:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-standard-options/#max
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-standard-options/#max
  add-a-field-override:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-overrides/#add-a-field-override
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-overrides/#add-a-field-override
  time-series:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/time-series/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/time-series/
---

# Bar chart

* bar chart
  * == rectangular bars /
    * 's length (height, width -- depends on -- vertical or horizontal bars) == value

* uses
  * compare data / DIFFERENT categories
    * Population distribution by age or location
    - CPU usage / application
    - SLO / Tribes
    - Sales / division

## Configure a bar chart

* [Youtube](https://www.youtube.com/watch?v=qyKE9-71KkE)
* _Example:_ [here](https://play.grafana.org/d/ktMs4D6Mk/)

## Supported data formats

* requirements
  * dataset / has 
    * 1 string OR time field (or column)
      * uses
        * label the bars 
    * \>=1 numeric field

### 1 row

| Group | Value1 | Value2 | Value3 |
| ----- | ------ | ------ | ------ |
| uno   | 5      | 3      | 2      |

### MULTIPLE rows

* displays
  * MULTIPLE bar chart groups

| Group | Value1 | Value2 | Value3 |
| ----- | ------ | ------ | ------ |
| uno   | 5      | 3      | 2      |
| dos   | 10     | 6      | 4      |
| tres  | 20     | 8      | 2      |

* if FIRST field is time-based -> use BETTER [time series visualization](ref:time-series)

* recommendations
  * ONLY use 1! dataset
    * Reason:🧠it can result in UNEXPECTED behavior🧠

## Apply ad hoc filters | bar chart 

* hover your cursor | bar,
  * display the filter button
  * click

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-adhoc-filter-icon-bar-v12.2.png" max-width="300px" alt="The ad hoc filter button in a bar chart tooltip">}}

## Configuration options

{{< docs/shared lookup="visualizations/config-options-intro.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Panel options

{{< docs/shared lookup="visualizations/panel-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Bar chart options

* DIFFERENT visualization look

| Option                          | Description                                                                                                                                                                                                                                                                                                 |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| X Axis                          | field / used for the x-axis                                                                                                                                                                                                                                                                                 |
| Orientation                     | == orientation values direction <br/> <ul><li>**Auto** <br/> &nbsp;&nbsp; Grafana selects AUTOMATICALLY the ideal orientation </li><li>**Horizontal** <br/> &nbsp;&nbsp; Bars stretch horizontally, left to right.</li> <li>**Vertical** <br/> &nbsp;&nbsp; Bars stretch vertically, top to bottom.</li></ul> |
| Rotate x-axis tick labels       | uses: bar chart labels are long                                                                                                                                                                                                                                                                             |
| X-axis tick label max length    | Sets the maximum length of bar chart labels. Labels longer than the maximum length are truncated, and appended with `...`.                                                                                                                                                                                  |
| X-axis labels minimum spacing   | minimum spacing BETWEEN x-axis labels <br/> <ul><li>**None** <br/> &nbsp;&nbsp; ALL tick marks are shown.</li> <br/> <li>**Small** <br/> &nbsp;&nbsp; 100 px of space</li><li>**Medium**<br/> &nbsp;&nbsp; == 200 px of space</li><li>**Large** <br/> &nbsp;&nbsp; == 300 px</li></ul>                      |
| Show values                     | whether values are shown \| top OR left of bars <br/> <ul><li>**Auto** <br/> &nbsp;&nbsp; if there is space -> displayed </li><li>**Always** <br/> &nbsp;&nbsp; ALWAYS </li><li>**Never** <br/> NEVER show values</li></ul>                                                                                 |
| Stacking                        | bar chart stacking == stack ALL values / SAME row <br/> <ul><li>**Off** <br/> &nbsp;&nbsp; NOT stacked</li><li>**Normal** <br/> &nbsp;&nbsp; stacked </li><li>**Percent** <br/> &nbsp;&nbsp; stacked  <br/> &nbsp;&nbsp; EACH bar's height == total height's percentage</li></ul>                           |
| Group width                     | width of groups (groups == DIFFERENT rows) <br/> 1 = Max with <br/> 0 = Min width                                                                                                                                                                                                                           |
| Bar width                       | width of bars (== EACH data) <br/> 1 = Max width <br/>0 = Min width                                                                                                                                                                                                                                         |
| Bar radius                      | radius of the bars <br/> <ul><li>0 = Minimum radius</li><li>0.5 = Maximum radius</li></ul>                                                                                                                                                                                                                  |
| Highlight full area on cover    | \| hover the bar, the entire surrounding area of the bar is highlighted                                                                                                                                                                                                                                     |
| Color by field                  | apply select field color \| ALL bar                                                                                                                                                                                                                                                                  |
| Line width                      | line width of the bars                                                                                                                                                                                                                                                                             |
| Fill opacity                    | fill opacity bars                                                                                                                                                                                                                                                                              |
| [Gradient mode](#gradient-mode) | Set the mode of the gradient fill. Fill gradient is based on the line color. To change the color, use the standard color scheme field option. Gradient appearance is influenced by the **Fill opacity** setting.                                                                                            |

<!-- prettier-ignore-end -->

#### Gradient mode

* [graph styles](/grafana/docs/sources/shared/visualizations/graph-styles-options.md)

### Tooltip options

{{< docs/shared lookup="visualizations/tooltip-options-1.md" source="grafana" version="<GRAFANA_VERSION>" leveloffset="+1" >}}

### Legend options

{{< docs/shared lookup="visualizations/legend-options-1.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Text size

Enter a **Value** to change the size of the text on your bar chart.

### Axis

Use the following field settings to refine how your axes display.

For guidance on configuring more than one y-axis, refer to [Multiple y-axes](#multiple-y-axes).

Some field options will not affect the visualization until you click outside of the field option box you are editing or press Enter.

<!-- prettier-ignore-start -->

| Option                                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|-------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Placement                                       | Y-axis placement <br/> <br/> <ul><li>**Auto** <br/> &nbsp;&nbsp; Grafana AUTOMATICALLY assigns <br/> &nbsp;&nbsp; if there are >=2 series / different units -> left axis == FIRST unit & right axis == following units </li><li>**Left** <br/> &nbsp;&nbsp; ALL Y-axes \| left side </li><li>**Right** <br/> ALL Y-axes \| right side </li><li>**Hidden** <br/> hide ALL axes <br/> if you want to SELECTIVELY hide axes -> [add a field override](ref:add-a-field-override)</li></ul> |
| Label                                           | Y-axis text label <br/> if you have >= 1 Y-axis -> assign DIFFERENT labels -- with an -- override                                                                                                                                                                                                                                                                                                                                                                                      |
| Width                                           | fixed width of the axis <br/> by default, Grafana DYNAMICALLY calculates </br>                                                                                                                                                                                                                                                                                                                                                                                                         |
| Show grid lines                                 | whether display grid lines <br/> <ul><li>**Auto** <br/> &nbsp;&nbsp; Grafana AUTOMATICALLY determines to display</li><li>**On** <br/> display </li><li>**Off** <br/> NO </li></ul>                                                                                                                                                                                                                                                                                                     |
| Color                                           | -- based on -- **Text** or **Series** color                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Show border                                     | hide or display the border                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Scale                                           | how the y-axis is split <br/> <ul><li>**Linear**</li><li>**Logarithmic** <br/>log base 2 or log base 10</li><li>**Symlog** <br/> symmetrical logarithmic scale <br/> log base 2 or log base 10</li></ul>                                                                                                                                                                                                                                                                               |
| Centered zero                                   | requirements: negative values <br/> y-axis so it's centered on zero.                                                                                                                                                                                                                                                                                                                                                                                                           |
| [Soft min and soft max](#soft-min-and-soft-max) | Set a **Soft min** or **soft max** option for better control of Y-axis limits. By default, Grafana sets the range for the Y-axis automatically based on the dataset.                                                                                                                                                                                                                                                                                                                   |

<!-- prettier-ignore-end -->

#### Soft min and soft max

Set a **Soft min** or **soft max** option for better control of Y-axis limits. By default, Grafana sets the range for the Y-axis automatically based on the dataset.

**Soft min** and **soft max** settings can prevent blips from turning into mountains when the data is mostly flat, and hard min or max derived from standard min and max field options can prevent intermittent spikes from flattening useful detail by clipping the spikes past a defined point.

You can set standard min/max options to define hard limits of the Y-axis. For more information, refer to [Standard options definitions](ref:standard-options-definitions).

{{< docs/shared lookup="visualizations/multiple-y-axes.md" source="grafana" version="<GRAFANA_VERSION>" leveloffset="+3" >}}

### Standard options

{{< docs/shared lookup="visualizations/standard-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Data links and actions

{{< docs/shared lookup="visualizations/datalink-options-2.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Value mappings

{{< docs/shared lookup="visualizations/value-mappings-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Thresholds

{{< docs/shared lookup="visualizations/thresholds-options-1.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Field overrides

{{< docs/shared lookup="visualizations/overrides-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}
