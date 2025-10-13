---
aliases:
  - ../../features/panels/table_panel/
  - ../../panels/visualizations/table/filter-table-columns/
  - ../../reference/table/
  - ../../visualizations/table/
  - ../../visualizations/table/filter-table-columns/
  - /docs/grafana/next/panels/visualizations/table/table-field-options/
description: Configure options for Grafana's table visualization
keywords:
  - grafana
  - dashboard
  - panels
  - table panel
  - table options
  - format tables
  - table filter
  - filter columns
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Table
weight: 100
refs:
  calculations:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/calculation-types/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/calculation-types/
  time-series-panel:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/time-series/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/time-series/
  time-series-to-table-transformation:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/transform-data/#time-series-to-table-transform
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/transform-data/#time-series-to-table-transform
  color-scheme:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-standard-options/#color-scheme
    - pattern: /docs/grafana-cloud
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-standard-options/#color-scheme
  field-override:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-overrides/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-overrides/
  data-transformation:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/transform-data/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/transform-data/
  build-query:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/
  graph-styles:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/time-series/#graph-styles-options
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/time-series/#graph-styles-options
---

# Table

* Tables
  * highly flexible
  * allows
    * display data | columns & rows
      * 👀EACH table cell can be visualized 👀-- as --
        * colored text
        * gauges,
        * sparklines,
        * data links,
        * JSON code,
        * images
  * uses
    * MULTIPLE datasets
      * Common database queries like logs, traces, metrics
      - Financial reports
      - Customer lists
      - Product catalogs
      - spreadsheet

* NOT support
  * Annotations
  * alerts

## Configure a table visualization

* [Youtube](https://www.youtube.com/watch?v=PCY7O8EJeJY)
* _Example:_ [here](https://play.grafana.org/d/OhR1ID6Mk/)

## Supported data formats

* 's input
  * data / has column-row structure

### if a cell is missing OR table column-row structure is NOT complete -> table visualization does NOT display any of the data

```csv
Column1, Column2, Column3
value1 , value2 , value3
gap1   , gap2
value4 , value5 , value6
```

### you can hide columns

* ways
  * [data transformations](ref:data-transformation),
  * [field overrides](#field-overrides)
  * [building a query](ref:build-query)

## Column filtering

* requirements
  * Table > Column filter > enable

* steps
  * Dashboard > choose 1 > edit panel > hover cursor | column's title > toggle on the [**Column filter** switch](#table-options)

## Apply ad hoc filters | table

* hover your cursor | cell
* see [Dashboard drilldown with ad hoc filters](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/dashboards/variables/add-template-variables/#dashboard-drilldown-with-ad-hoc-filters)

## Sort columns

* | EACH column title,
  * click to change sort order

## Dataset selector

* requirements
  * MULTIPLE datasets
  * edit panel

* == | bottom,
  * drop-down list at the bottom, to select the dataset

## Configuration options

### Panel options

{{< docs/shared lookup="visualizations/panel-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Table options

<!-- prettier-ignore-start -->
| Option               | Description                                                                                                                                                                                                                                                                 |
| -------------------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Show table header    | Show or hide column names imported from your data source.                                                                                                                                                                                                                   |
| Frozen columns       | Freeze columns -- from the -- left side <br/> == NUMBER of columns to freeze                                                                                                                                                                                                |
| Cell height          | cell height of the cell                                                                                                                                                                                                                                                     |
| Max row height       | maximum height / row in the table <br/> uses **Wrap text**                                                                                                                                                                                                                  |
| Enable pagination    | Toggle the switch to control how many table rows are visible at once. When switched on, the page size automatically adjusts to the height of the table. This option doesn't affect queries.                                                                                 |
| Minimum column width | Define the lower limit of the column width, in pixels. By default, the minimum width of the table column is 150 pixels. For small-screen devices, such as mobile phones or tablets, reduce the value to `50` to allow table-based panels to render correctly in dashboards. |
| Column width         | Define a column width, in pixels, rather than allowing the width to be set automatically. By default, Grafana calculates the column width based on the table size and the minimum column width.                                                                             |
| Column alignment     | Set how Grafana should align cell contents. Choose from: **Auto** (default), **Left**, **Center**, or **Right**.                                                                                                                                                            |
| Column filter        | Temporarily change how column data is displayed                                                                                                                                                                                                                             |
| Wrap text            | Enables text wrapping for cell content.                                                                                                                                                                                                                                     |
| Wrap header text     | Enables text wrapping for column headers.                                                                                                                                                                                                                                   |
<!-- prettier-ignore-end -->

### Table footer options

The table footer displays the results of calculations (and reducer functions) on fields.
The footer is only displayed after you select an option in the **Calculation** drop-down list:

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-table-footer-selector-v12.2.png" max-width="300px" alt="The footer calculation selector, open" >}}

There are several calculations you can choose from including minimum, maximum, first, last, and total.
For the full list of options, refer to [Calculations](ref:calculations).

In the table footer:

- You can apply multiple calculations at once.
- The calculations and reducer functions apply to all fields in the table, by default. To control which fields have a calculation or function applied, add the table footer in an override instead.
- If you enable a mathematical function for a non-numeric field, nothing for that function is displayed for that field.

In the following image, multiple calculations&mdash;**Mean**, **Max**, and **Last**&mdash;have been applied:

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-tablefooter-v12.2.png" max-width="750px" alt="Table with footer displaying mean, max, and last" >}}

You can also see in the previous image that the mathematical functions, **Mean** and **Max**, haven't been applied to the text field in the table.
Only the **Last** function has been applied to that field.

{{< admonition type="note">}}
Calculations applied to cell types like **Markdown + HTML** might have unexpected results.
{{< /admonition>}}

### Cell options

* how data is displayed | table
  * -- depends on -- cell type

#### Cell type

* apply | ALL cells
  * if you want to apply | 1! cell type -> Override > choose 1 column > Cell type

<!-- prettier-ignore-start -->
| Cell type                                 | Description                                                                                                                                               |
| ----------------------------------------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Auto](#auto)                             | == basic text + number cell                                                                                                                               |
| [Colored text](#colored-text)             | If thresholds, value mappings, or color schemes are set, then the cell text is displayed in the appropriate color.                                        |
| [Colored background](#colored-background) | If thresholds, value mappings, or color schemes are set, then the cell background is displayed in the appropriate color.                                  |
| [Data links](#data-links)                 | The cell text reflects the titles of the configured data links.                                                                                           |
| [Gauge](#gauge)                           | Values are displayed as a horizontal bar gauge. You can set the [Gauge display mode](#gauge-display-mode) and the [Value display](#value-display) options. |
| [Sparkline](#sparkline)                   | Shows values rendered as a sparkline.                                                                                                                     |
| [JSON View](#json-view)                   | Shows values formatted as code.                                                                                                                           |
| [Pill](#pill)                             | Displays each item in a comma-separated string in a colored block.                                                                                        |
| [Markdown + HTML](#markdown--html)        | Displays rich markdown or HTML content.                                                                                                                   |
| [Image](#image)                           | Displays an image when the value is a URL or a base64 encoded image.                                                                                      |
| [Actions](#actions)                       | The cell displays a button that triggers a basic, unauthenticated API call when clicked.                                                                  |
<!-- prettier-ignore-end -->

#### Auto

{{< docs/shared lookup="visualizations/cell-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

#### Colored text

If thresholds, value mappings, or color schemes are set, the cell text is displayed in the appropriate color.

![Table with colored text cell type](/media/docs/grafana/panels-visualizations/screenshot-table-colored-text-v11.3-2.png)

The colored text cell type has the following options:

{{< docs/shared lookup="visualizations/cell-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

#### Colored background

If thresholds, value mappings, or color schemes are set, the cell background is displayed in the appropriate color.

![Table with colored background cell type](/media/docs/grafana/panels-visualizations/screenshot-table-colored-bkgrnd-v11.3-2.png)

You can also set background cell color by row:

![Table with background cell color applied to row](/media/docs/grafana/panels-visualizations/screenshot-table-colored-row-v11.3.png)

The colored background cell type has the following options:

<!-- prettier-ignore-start -->
| Option | Description |
| ------ | ----------- |
| Background display mode | Choose between **Basic** and **Gradient**. |
| Apply to entire row | Toggle the switch on to apply the background color that's configured for the cell to the whole row. |
| Cell value inspect | <p>Enables value inspection from table cells. When the switch is toggled on, clicking the inspect icon in a cell opens the **Inspect value** drawer which contains two tabs: **Plain text** and **Code editor**.</p><p>Grafana attempts to automatically detect the type of data in the cell and opens the drawer with the associated tab showing. However, you can switch back and forth between tabs.</p> |
| Tooltip from field | Toggle on the **Tooltip from field** switch to use the values from another field (or column) in a tooltip. For more information, refer to the [Tooltip from field](#tooltip-from-field). |
<!-- prettier-ignore-end -->

<!-- The cell value inspect and tooltip from field descriptions above should be copied from docs/sources/shared/visualizations/cell-options.md -->

#### Data links

If you've configured data links, when the cell type is **Auto**, the cell text becomes clickable.
If you change the cell type to **Data links**, the cell text reflects the titles of the configured data links. To control the application of data link text more granularly, use a **Cell option > Cell type > Data links** field override.

#### Gauge

* cell type
  * displayed -- as a -- graphical gauge

<!-- prettier-ignore-start -->
| Option             | Description                                                                                                                                                                        |
| ------------------ |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Gauge display mode | [Gauge display mode](#gauge-display-mode)                                                                                                                                          |
| Value display      | how display the value <br/> [Value display](#value-display)                                                                                                                        |
| Tooltip from field | **Tooltip from field** switch to use the values from another field (or column) in a tooltip <br/> [Tooltip from field](#tooltip-from-field). |
<!-- prettier-ignore-end -->

{{< admonition type="note" >}}
The maximum and minimum values of the gauges are configured automatically from the smallest and largest values in your whole dataset.
If you don't want the max/min values to be pulled from the whole dataset, you can configure them for each column using [field overrides](#field-overrides).
{{< /admonition >}}

##### Gauge display mode

You can set three gauge display modes.

<!-- prettier-ignore-start -->
| Option    | Description                                      |
|-----------|--------------------------------------------------|
| Basic     | threshold levels -- define the -- color of gauge |
| Gradient  | threshold levels -- define a -- gradient         |
| Retro LCD | gauge is split up \| small cells                 |
<!-- prettier-ignore-end -->

##### Value display

Labels displayed alongside of the gauges can be set to be colored by value, match the theme text color, or be hidden.

<!-- prettier-ignore-start -->
| Option | Description |
| ------ | ----------- |
| Value color | Labels are colored by value. {{< figure src="/media/docs/grafana/panels-visualizations/screenshot-labels-value-color-v11.3.png" alt="Table with labels in value color" >}} |
| Text color | Labels match the theme text color. {{< figure src="/media/docs/grafana/panels-visualizations/screenshot-labels-text-color-v11.3.png" alt="Table with labels in theme color" >}} |
| Hidden | Labels are hidden. {{< figure src="/media/docs/grafana/panels-visualizations/screenshot-labels-hidden-v11.3.png" alt="Table with labels hidden" >}} |
<!-- prettier-ignore-end -->

#### Sparkline

This cell type shows values rendered as a sparkline.
To show sparklines on data with multiple time series, use the [Time series to table transformation](ref:time-series-to-table-transformation) to process it into a format the table can show.

![Table using sparkline cell type](/media/docs/grafana/panels-visualizations/screenshot-table-as-sparkline-v11.3.png)

The sparkline cell type options are described in the following table.
For more detailed information about all of the sparkline styling options (except **Hide value**), refer to the [time series graph styles documentation](ref:graph-styles).

<!-- prettier-ignore-start -->
| Option              | Description                                                                |
| ------------------- | --------------------------------------------------------------------------------------------- |
| Hide value          | Toggle the switch on or off to display or hide the cell value on the sparkline. |
| Style               | Choose whether to display your time-series data as **Lines**, **Bars**, or **Points**. You can use overrides to combine multiple styles in the same graph. |
| Line interpolation  | How the graph interpolates the series line. Choose from:<ul><li>**Linear** - Points are joined by straight lines.</li><li>**Smooth** - Points are joined by curved lines that smooths transitions between points.</li><li>**Step before** - The line is displayed as steps between points. Points are rendered at the end of the step.</li><li>**Step after** - The line is displayed as steps between points. Points are rendered at the beginning of the step.</li></ul> |
| Line width          | The thickness of the series lines or the outline for bars using the **Line width** slider. |
| Fill opacity        | The series area fill color using the **Fill opacity** slider. |
| Gradient mode       | Gradient mode controls the gradient fill, which is based on the series color. Gradient appearance is influenced by the **Fill opacity** setting. To change the color, use the standard color scheme field option. For more information, refer to [Color scheme](ref:color-scheme). Choose from:<ul><li>**None** - No gradient fill. This is the default setting.</li><li>**Opacity** - An opacity gradient where the opacity of the fill increases as y-axis values increase.</li><li>**Hue** - A subtle gradient that's based on the hue of the series color.</li></ul>                                                                                                    |
| Line style          | Choose from:<ul><li>**Solid**</li><li>**Dash** - Select the length and gap for the line dashes. Default dash spacing is 10, 10.</li><li>**Dots** - Select the gap for the dot spacing. Default dot spacing is 0, 10.</li></ul> |
| Connect null values | How null values, which are gaps in the data, appear on the graph. Null values can be connected to form a continuous line or set to a threshold above which gaps in the data are no longer connected. Choose from:<ul><li>**Never** - Time series data points with gaps in the data are never connected.</li><li>**Always** - Time series data points with gaps in the data are always connected.</li><li>**Threshold** - Specify a threshold above which gaps in the data are no longer connected. This can be useful when the connected gaps in the data are of a known size or within a known range, and gaps outside this range should no longer be connected.</li></ul> |
| Show points         | Whether to show data points to lines or bars. Choose from: <ul><li>**Auto** - Grafana determines a point's visibility based on the density of the data. If the density is low, then points appear.</li><li>**Always** - Show the points regardless of how dense the dataset is.</li><li>**Never** - Don't show points.</li></ul> |
| Point size          | Set the size of the points, from 1 to 40 pixels in diameter. |
| Bar alignment       | Set the position of the bar relative to a data point. |
| Tooltip from field | Toggle on the **Tooltip from field** switch to use the values from another field (or column) in a tooltip. For more information, refer to [Tooltip from field](#tooltip-from-field). |
<!-- prettier-ignore-end -->

#### JSON View

This cell type shows values formatted as code.
If a value is an object the JSON view allowing browsing the JSON object will appear on hover.

{{< figure src="/static/img/docs/tables/json-view.png" max-width="350px" alt="JSON view" class="docs-image--no-shadow" >}}

For the JSON view cell type, you can set enable **Cell value inspect**.
This enables value inspection from table cells.
When the switch is toggled on, clicking the inspect icon in a cell opens the **Inspect value** drawer which contains two tabs: **Plain text** and **Code editor**.

Toggle on the **Tooltip from field** switch to use the values from another field (or column) in a tooltip.
For more information, refer to [Tooltip from field](#tooltip-from-field).

Grafana attempts to automatically detect the type of data in the cell and opens the drawer with the associated tab showing.
However, you can switch back and forth between tabs.

#### Pill

The **Pill** cell type displays each item in a comma-separated string in a colored block.

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-table-pill-cells-v12.2.png" max-width="750px" alt="Table using the pill cell type" >}}

The colors applied to each piece of text are maintained throughout the table.
For example, if the word "test" is first displayed in a red pill, it will always be displayed in a red pill.

The following data formats are supported for the pill cell type:

- Comma-separated values (`cows,chickens,goats`)
- JSON arrays of uniform (`(["cows","chickens","goats"])`) or mixed (`[1,2,3,"foo",42,"bar"]`) types

Toggle on the **Tooltip from field** switch to use the values from another field (or column) in a tooltip.
For more information, refer to [Tooltip from field](#tooltip-from-field).

#### Markdown + HTML

The **Markdown + HTML** cell type displays rich Markdown or HTML content, rendered using the
[GitHub-Flavored Markdown](https://github.github.com/gfm/) spec. This is useful if you need to display
customized, pre-formatted information alongside tabular data, such as formatted strings,
lists of links, or other dynamic cases.

For this cell type, you can toggle the **Dynamic height** switch, which allows the cell to resize
dynamically based on the cell content. If you use dynamic height, we strongly recommend that you
also toggle on **Pagination** to avoid performance issues in larger tables, since enabling
Dynamic height disables table {{< term "virtualization" >}}virtualization{{< /term >}}.

By default, the HTML rendered is sanitized, and un-sanitized HTML can only be rendered
in these cells if the [`disable_sanitize_html`](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#disable_sanitize_html) option is set to true for your Grafana instance.

Toggle on the **Tooltip from field** switch to use the values from another field (or column) in a tooltip.
For more information, refer to [Tooltip from field](#tooltip-from-field).

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-table-markdown-v12.2.png" max-width="600px" alt="Table using the pill cell type" >}}

#### Image

If you have a field value that is an image URL or a base64 encoded image, this cell type displays it as an image.

![Table with image cell type](/media/docs/grafana/panels-visualizations/screenshot-table-cell-image-v11.3.png)

It has the following options:

<!-- prettier-ignore-start -->
| Option             | Description                                                                                                                   |
| ------------------ |  ---------------------------------------------------------------------------------------------------------------------------- |
| Alt text           | Set the alternative text of an image. The text will be available for screen readers and in cases when images can't be loaded. |
| Title text         | Set the text that's displayed when the image is hovered over with a cursor. |
| Tooltip from field | Toggle on the **Tooltip from field** switch to use the values from another field (or column) in a tooltip. For more information, refer to [Tooltip from field](#tooltip-from-field). |
<!-- prettier-ignore-end -->

#### Actions

The cell displays a button that triggers a basic, unauthenticated API call when clicked.
Configure the API call with the following options:

<!-- prettier-ignore-start -->
| Option             | Description  |
| ------------------ | ------------ |
| Endpoint           | Enter the endpoint URL. |
| Method             | Choose from **GET**, **POST**, and **PUT**. |
| Content-Type       | Select an option in the drop-down list. Choose from: JSON, Text, JavaScript, HTML, XML, and x-www-form-urlencoded. |
| Query parameters   | Enter as many **Key**, **Value** pairs as you need. |
| Header parameters  | Enter as many **Key**, **Value** pairs as you need. |
| Payload            | Enter the body of the API call. |
| Tooltip from field | Toggle on the **Tooltip from field** switch to use the values from another field (or column) in a tooltip. For more information, refer to [Tooltip from field](#tooltip-from-field). |
<!-- prettier-ignore-end -->

#### Tooltip from field

Toggle on the **Tooltip from field** switch to use the values from another field (or column) in a tooltip.

When you toggle the switch on, you can select from a drop-down list any of the fields in the table to be used as the source of the tooltip content.
All table fields are included in the drop-down list, whether visible or hidden.

When a tooltip from a field has been added to a cell, a chip is displayed in the top-right or top-left corner of the cell:

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-tooltip-chip-1-v12.2.png" max-width="500px" alt="Tooltip chip" >}}

Hover your mouse over the chip to display the tooltip.

When you toggle on the switch, the **Tooltip placement** option, which controls where the tooltip box opens upon hover, is also displayed.
Select one of the following options: **Auto**, **Top**, **Right**, **Bottom**, and **Left**.

The content of the tooltip is determined by the values of the source field and can't be directly edited.
However, you can affect the display of the value using overrides like value mappings, as shown in the [Example: Tooltip from field with value mappings](#example-tooltip-from-field-with-value-mappings) section.

While you can turn on this option under **Cell options**, and have it applied to all cells in the table, it's typically used as an override on a sub-set of cells instead.
This is demonstrated in the example in the following section.

##### Example: Tooltip from field using overrides

The following table has five visible fields (columns) as well as a hidden field called "Info":

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-tooltip-table-1-v12.2.png" max-width="750px" alt="Table that includes a hidden column" >}}

- The "Info" field is hidden using the **Table > Hide in table** override property.
- The following overrides have been applied to the "Short text" field:
  - The values from the "Info" field are used as tooltip text for the "Short text" cells using the **Cell options > Tooltip from field** override property.
  - The **Cell options > Tooltip placement** override property is set to control the placement of the tooltip.

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-tooltip-override-2-v12.2.png" max-width="300px" alt="Override to use the Info field values as tooltips for the Short text column" >}}

Now, when you hover the cursor over the chip in the "Short text" column, the corresponding values from the "Info" column appear in the tooltip:

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-tooltip-on-hover-v12.2.png" max-width="750px" alt="Info field value in the tooltip of the Short text cell upon hover" >}}

##### Example: Tooltip from field with value mappings

While the content of the tooltip is determined by the values of the source field and can't be directly edited, you can use field overrides on the source field to manipulate the display of that value.

For example, if the "Info" column is being used as the source field for the tooltip values, you could set up a value mapping.
In this case, the value "up" is mapped to the word "Good":

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-tooltip-value-map-v12.2.png" max-width="750px" alt="Info field value up being mapped to the value Good in an override" >}}

Now, when you hover the cursor over the chip in the "Short text" cell, the mapped value appears in the tooltip:

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-tooltip-on-hover-2-v12.2.png" max-width="750px" alt="Info field mapped to a new value in the tooltip of the Short text cell upon hover" >}}

You can use all field overrides to affect the display of the tooltip.
For example, the **Table > Column width** or **Cell options > Cell type** overrides can change the cell width or visual display of the data.

### Standard options

{{< docs/shared lookup="visualizations/standard-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Data links and actions

{{< docs/shared lookup="visualizations/datalink-options-3.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Value mappings

{{< docs/shared lookup="visualizations/value-mappings-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Thresholds

{{< docs/shared lookup="visualizations/thresholds-options-2.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Field overrides

{{< docs/shared lookup="visualizations/overrides-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}
