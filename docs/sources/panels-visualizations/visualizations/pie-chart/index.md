---
aliases:
  - ../../panels/visualizations/pie-chart-pane/
  - ../../visualizations/pie-chart-panel/
keywords:
  - grafana
  - pie chart
labels:
  products:
    - cloud
    - enterprise
    - oss
description: Configure options for Grafana's pie chart visualization
title: Pie chart
weight: 100
refs:
  calculation-types:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/calculation-types/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/calculation-types/
  configure-legends:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-legend/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-legend/
---

# Pie chart

* pie chart
  * displays data -- as -- circle's segments / related to the whole
    * EACH slice == 1 value or measurement

* uses
  * compare data
    * Incident causes per category
    * Network traffic sources
    * User demographics

## Configure a pie chart visualization

* [Youtube](https://www.youtube.com/watch?v=A_lDhM9w4_g)
* _Example:_ [here](https://play.grafana.org/d/ktMs4D6Mk/)

## Supported data formats

* requirements
  * dataset / has a set of numeric values 
* display 1 pie
  * regardless of: number of datasets, fields, or records queried in it

### 1! value

* dataset / 1! record

| Value1 | Value2 | Value3 | Optional |
| ------ | ------ | ------ | -------- |
| 5      | 3      | 2      | Sums10   |

### MULTIPLE rows

| Value | Label  |
| ----- | ------ |
| 5     | Value1 |
| 3     | Value2 |
| 2     | Value3 |

* requirements
  * Value options > **Show** == **All values**

### Multiple rows & columns

If your dataset contains multiple rows and columns with numeric data, by default only the last row's values are summed.

| Value1 | Value2 | Value3 | Optional |
| ------ | ------ | ------ | -------- |
| 5      | 3      | 2      | Sums10   |
| 10     | 6      | 4      | Sums20   |
| 20     | 8      | 2      | Sums30   |

![Pie chart visualization with multiple rows and columns showing the last one](/media/docs/grafana/panels-visualizations/screenshot-grafana-12.1-pie-example4.png)

If you want to display all the cells, change the **Show** setting in the [Value options](#value-options) from **Calculate** to **All values**. This also labels the elements by concatenating all the text fields (if you have any) with the column name.

![Pie chart visualization with multiple rows and columns showing the all values](/media/docs/grafana/panels-visualizations/screenshot-grafana-12.1-pie-example5.png)

If you want to display only the values from a given field (or column), once the **Show** setting in the [Value options](#value-options) is set to **All values**, set the **Fields** option to the column you wish to sum in the display. The value labels are also concatenated as indicated before.

![Pie chart visualization with multiple rows and columns showing values from one column](/media/docs/grafana/panels-visualizations/screenshot-grafana-12.1-pie-example6.png)

## Configuration options

{{< docs/shared lookup="visualizations/config-options-intro.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Panel options

{{< docs/shared lookup="visualizations/panel-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Value options

* uses
  * refine how your visualization displays its values

| Option      | Description                                                                                                                                                                                         |
|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Show        | <ul><li>**Calculate** <br/> &nbsp;&nbsp; display 1! value -- based on -- ALL rows</li><li>**All values** <br/> &nbsp;&nbsp; display SEPARATE stat / EACH row                                        |
| Calculation | requirements: show == **Calculate** <br/> == reducer function / Grafana use to reduce MANY fields -- to -- 1! value <br/> [Calculation types](ref:calculation-types) |
| Limit       | requirements: show == **All values** <br/> == MAXIMUM number of rows / display                                                                                                                      |
| Fields      | field / display \| visualization  <br/>  &nbsp;&nbsp; -- depend on -- AVAILABLE fields                                                                                                              |

### Pie chart options

* DIFFERENT visualization look

#### Pie chart type

**Pie** or **Donut**.

#### Slice sorting

- **Descending** 
  - slices decrease in size
    - clockwise (FROM 00:00)
- **Ascending**
  - slices increase in size
    - clockwise (FROM 00:00)
- **None** 
  - original order of the data

#### Labels

* labels / display | pie chart
  * MULTIPLE can be selected

- **Name** - The series or field name.
- **Percent** - The percentage of the whole.
- **Value** - The raw numerical value.

Labels are displayed in white over the body of the chart

### Tooltip options

{{< docs/shared lookup="visualizations/tooltip-options-1.md" source="grafana" version="<GRAFANA_VERSION>" leveloffset="+1" >}}

### Legend options

Use these settings to define how the legend appears in your visualization. For more information about the legend, refer to [Configure a legend](ref:configure-legends).

<!-- prettier-ignore-start -->

| Option | Description |
| ------ | ----------- |
| Visibility | Toggle the switch to turn the legend on or off. |
| Mode | Use these settings to define how the legend appears in your visualization. Choose from:<ul><li>**List** - Displays the legend as a list. This is a default display mode of the legend.</li><li>**Table** - Displays the legend as a table.</li></ul> |
| Placement | Select where to display the legend. Choose **Bottom** or **Right**. |
| Width | Control how wide the legend is when placed on the right side of the visualization. This option is only displayed if you set the legend placement to **Right**. |
| Legend values | Select values to display in the legend. You can select more than one:<ul><li>**Percent** - The percentage of the whole.</li><li>**Value** - The raw numerical value.</li></ul> |

<!-- prettier-ignore-end -->

### Standard options

{{< docs/shared lookup="visualizations/standard-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Data links and actions

{{< docs/shared lookup="visualizations/datalink-options-1.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Value mappings

{{< docs/shared lookup="visualizations/value-mappings-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Field overrides

{{< docs/shared lookup="visualizations/overrides-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}
