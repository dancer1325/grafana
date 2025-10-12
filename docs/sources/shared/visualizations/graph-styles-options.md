---
title: Graph styles options
comments: |
  This file is used in the following visualizations: time series.
---

<!-- prettier-ignore-start -->

| Option                                        | Description                                                                                                                                                                                                                          |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Style](#style)                               | display your time-series data -- as -- **Lines**, **Bars**, or **Points**                                                                                                                                                            |
| [Line interpolation](#line-interpolation)     | Choose how the graph interpolates the series line.                                                                                                                                                                                   |
| Line width                                    | Set the thickness of the series lines or the outline for bars using the **Line width** slider.                                                                                                                                       |
| Fill opacity                                  | Set the series area fill color using the **Fill opacity** slider.                                                                                                                                                                    |
| [Gradient mode](#gradient-mode)               | Choose a gradient mode to control the gradient fill, which is based on the series color.                                                                                                                                             |
| [Line style](#line-style)                     | Choose a solid, dashed, or dotted line style.                                                                                                                                                                                        |
| [Connect null values](#connect-null-values)   | Choose how null values, which are gaps in the data, appear on the graph.                                                                                                                                                             |
| [Disconnect values](#disconnect-values)       | Choose whether to set a threshold above which values in the data should be disconnected.                                                                                                                                             |
| [Show points](#show-points)                   | Set whether to show data points to lines or bars.                                                                                                                                                                                    |
| Point size                                    | Set the size of the points, from 1 to 40 pixels in diameter.                                                                                                                                                                         |
| [Stack series](#stack-series)                 | Set whether Grafana displays series on top of each other.                                                                                                                                                                            |
| [Bar alignment](#bar-alignment)               | Set the position of the bar relative to a data point.                                                                                                                                                                                |
| Bar width factor                              | Set the width of the bar relative to minimum space between data points. A factor of 0.5 means that the bars take up half of the available space between data points. A factor of 1.0 means that the bars take up all available space. |

<!-- prettier-ignore-end -->

#### Style

* uses
  * | time-series

* ALLOWED options
  * **Lines**,
  * **Bars**,
  * **Points**

#### Line interpolation

* requirements
  * style = lines

* way to interpolate the serie
  - **Linear**
    - points / joined -- by -- straight lines
  - **Smooth** 
    - points / joined -- by -- curved lines == smooths transitions
  - **Step before**
    - line == steps BETWEEN points /
      - points are rendered | end of the step
  - **Step after** 
    - line == steps BETWEEN points /
      - points are rendered | beginning of the step

#### Gradient mode

* requirements
  * style = lines OR bars

* gradient fill
  * == 👀fill the area BETWEEN line -- & -- axis X👀 /
    * degraded colour

* control the gradient fill 
  * -- based on the -- series color & **Fill opacity**
  * ALLOWED values
    - **None** 
      - NO gradient fill
      - default
    - **Opacity**
      - increases -- proportionally to -- y-axis
    - **Hue**
      - A subtle gradient that's based on the hue of the series color.
    - **Scheme**
      - -- based on -- your [Color scheme](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-standard-options/#color-scheme)
      - used | fill area -- & -- line
      - see [Scheme gradient mode](#scheme-gradient-mode)

##### Scheme gradient mode

* TODO:
In **Scheme** gradient mode, the line or bar receives a gradient color defined from the selected **Color scheme** option in the visualization's **Standard** options.

The following image shows a line chart with the **Green-Yellow-Red (by value)** color scheme option selected:

{{< figure src="/static/img/docs/time-series-panel/gradient_mode_scheme_line.png" max-width="600px" alt="Color scheme: Green-Yellow-Red" >}}

If the **Color scheme** is set to **From thresholds (by value)** and **Gradient mode** is set to **Scheme**, then the line or bar color changes as it crosses the defined thresholds:

{{< figure src="/static/img/docs/time-series-panel/gradient_mode_scheme_thresholds_line.png" max-width="600px" alt="Colors scheme: From thresholds" >}}

#### Line style

* requirements
  * style = lines

* ALLOWED values
  - **Solid** 
    - == solid line
    - default
  - **Dash** 
    - == dashed line
      - == (length, gap) / line dashes
        - by default,
          - 10, 10 
  - **Dots**
    - == dotted lines
      - == (length = 0, gap) for the dot spacing
        - by default,
          - 0, 10 

#### Show points

* requirements
  * style = lines

* == shot real data points

* ALLOWED values
  - **Auto**
    - point's visibility -- based on the -- density of the data (== space BETWEEN data points)
      - if the density is low -> points appear
  - **Always**
    - show ALWAYS the data points
      - -- regardless of -- density of the data
  - **Never**
    - NOT show

#### Stack series

* TODO: 
Set whether Grafana stacks or displays series on top of each other. Be cautious when using stacking because it can create misleading graphs. To read more about why stacking might not be the best approach, refer to [The issue with stacking](https://www.data-to-viz.com/caveat/stacking.html). Choose from the following:

- **Off** - Turns off series stacking. When **Off**, all series share the same space in the visualization.
- **Normal** - Stacks series on top of each other.
- **100%** - Stack by percentage where all series add up to 100%.

##### Stack series in groups

The stacking group option is only available as an override. For more information about creating an override, refer to [Configure field overrides](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-overrides/).

1. Edit the panel and click **Overrides**.
1. Create a field override for the **Stack series** option.
1. In stacking mode, click **Normal**.
1. Name the stacking group in which you want the series to appear.

   The stacking group name option is only available when you create an override.

#### Bar alignment

Set the position of the bar relative to a data point. In the examples below, **Show points** is set to **Always** which makes it easier to see the difference this setting makes. The points don't change, but the bars change in relationship to the points. Choose from the following:

- **Before** ![Bar alignment before icon](/static/img/docs/time-series-panel/bar-alignment-before.png)
  The bar is drawn before the point. The point is placed on the trailing corner of the bar.
- **Center** ![Bar alignment center icon](/static/img/docs/time-series-panel/bar-alignment-center.png)
  The bar is drawn around the point. The point is placed in the center of the bar. This is the default.
- **After** ![Bar alignment after icon](/static/img/docs/time-series-panel/bar-alignment-after.png)
  The bar is drawn after the point. The point is placed on the leading corner of the bar.
