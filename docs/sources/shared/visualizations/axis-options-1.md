---
title: Axis options
comments: |
  There are three axis options shared files, axis-options-1.md, axis-options-2.md, and axis-options-3.md to cover the most common combinations of options. 
  Using shared files ensures that content remains consistent across visualizations that share the same options and users don't have to figure out which options apply to a specific visualization when reading that content.
  This file is used in the following visualizations: time series.
---

* scope
  * x- & y-axes

* if you want to make effective some change -> click OUTSIDE of the field option box

<!-- prettier-ignore-start -->

| Option                               | Description                                                                                                       |
|--------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| Time zone                            | Set the desired time zones to display along the x-axis. Choose from: **Auto**, **Left**, **Right**, and **Hidden**. |
| [Placement](#placement)              | y-axis placement                                                                                                  |
| Label                                | y-axis text label <br/> if you have >1 y-axis -> assign DIFFERENT labels -- via -- override                       |
| Width                                | axis' fixed width <br/> by default, Grafana DYNAMICALLY calculates it                                             |
| Show grid lines                      | axis grid line visibility                                                                                         |
| Color                                | == color of the axis <br/> **Text** == panel text color <br/> **Series** == colors of the series                  |
| Show border                          | == y-axis border visibility                                                                                       |
| [Scale](#scale)                      | == y-axis values scale <br/> ALLOWED values: **Linear**, **Logarithmic**, and **Symlog**                          |
| Centered zero                        | y-axis / it's centered \| 0                                                                                       |
| [Soft min](#soft-min-and-soft-max)   | control the y-axis limits                                                                |
| [Soft max](#soft-min-and-soft-max)   | control the y-axis limits                                                                |

<!-- prettier-ignore-end -->

#### Placement

Select the placement of the y-axis. Choose from the following:

- **Auto** - Automatically assigns the y-axis to the series. When there are two or more series with different units, Grafana assigns the left axis to the first unit and the right axis to the units that follow.
- **Left** - Display all y-axes on the left side.
- **Right** - Display all y-axes on the right side.
- **Hidden** - Hide all axes. To selectively hide axes, [Add a field override](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-overrides/#add-a-field-override) that targets specific fields.

#### Scale

- **Linear**
  - scale split into EQUAL parts
- **Logarithmic**
  - logarithmic scale
  - ALLOWED options
    - binary (== base 2)
    - base 10
- **Symlog** 
  - == symmetrical logarithmic scale
  - TODO:When you select this option, a list appears for you to choose a binary (base 2) or common (base 10) logarithmic scale
  - The linear threshold option allows you to set the threshold at which the scale changes from linear to logarithmic.

#### Soft min and soft max

* AUTOMATICALLY,
  * set by Grafana

* uses
  * 💡identify pretty small changes VISUALLY == anomalies💡

* != hard min & max values

* MORE [Configure standard options](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-standard-options/#max).
