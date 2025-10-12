---
aliases:
  - ../../features/panels/histogram/
  - ../../panels/visualizations/time-series/
  - ../../panels/visualizations/time-series/annotate-time-series/
  - ../../panels/visualizations/time-series/change-axis-display/
  - ../../panels/visualizations/time-series/graph-color-scheme/
  - ../../panels/visualizations/time-series/graph-time-series-as-bars/
  - ../../panels/visualizations/time-series/graph-time-series-as-lines/
  - ../../panels/visualizations/time-series/graph-time-series-as-points/
  - ../../panels/visualizations/time-series/graph-time-series-stacking/
  - ../../visualizations/time-series/
  - ../../visualizations/time-series/annotate-time-series/
  - ../../visualizations/time-series/change-axis-display/
  - ../../visualizations/time-series/graph-color-scheme/
  - ../../visualizations/time-series/graph-time-series-as-bars/
  - ../../visualizations/time-series/graph-time-series-as-lines/
  - ../../visualizations/time-series/graph-time-series-as-points/
  - ../../visualizations/time-series/graph-time-series-stacking/
keywords:
  - grafana
  - graph panel
  - time series panel
  - documentation
  - guide
  - graph
labels:
  products:
    - cloud
    - enterprise
    - oss
description: Configure options for Grafana's time series visualization
title: Time series
menuTitle: Time series
weight: 10
refs:
  link-alert:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-grafana-managed-rule/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-grafana-managed-rule/
  panel-data-section:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/panel-editor-overview/#data-section
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/panel-editor-overview/#data-section
---

# Time series

* Time series visualizations
  * == default way / show the variations of a set of data values | time
  * == x-y graph
    * 💡data point💡 
      * == numerical data | axis Y
        * if there are >1 numerical data -> EACH one is plotted | NEW line, point, or bar labeled
    * time | axis X
  * == 👀[_time series_ / renders -- as -- lines, points, or bars](#graph-styles-options)👀 

    ![](/grafana/media/docs/panels-visualizations/screenshot-time-series-v12.0.png)
  * uses
    * 💡display large numbers of timed data points / hard to track | table or list💡
  * _Examples:_
    - Temperature variations | day
    - daily progress of your retirement account
    - distance you jog each day | course of a year

* legacy Graph visualization (TODO:❓)
  * can be migrated -- to the -- time series visualization

## Configure a time series visualization

* [Youtube](https://www.youtube.com/watch?v=RKtW87cPxsw)
  * [Grafana playground](https://play.grafana.org/d/000000016/)

## Supported data formats

* requirements
  * time-series data—a sequence of measurements /
    * ordered | time
      * if the time field is NOT AUTOMATICALLY detected -> convert the data -- , via [data transformation](ref:panel-data-section), to a -- time format 
    * formatted -- as a -- table /
      * 's row == 1! measurement | specific time

## Alert rules

* [link alert rules](ref:link-alert)

## Special overrides

### Transform override property

* allows
  * transform series values 
    * WITHOUT affecting the values | tooltip, context menu, or legend
* Add field override > whatever > **Graph styles > Transform** [override property](#field-overrides)

* ALLOWED values
  - **Constant**
    - FIRST value == constant line
  - **Negative Y transform** 
    - results | y-axis
      - are flipped -- to -- negative values 

### Fill below to override property

* allows
  * fills the area BETWEEN 2 series /
    * ⚠️select the series | fill BELOW⚠️
* Add field override > whatever > **Graph styles > Fill below to** [override property](#field-overrides)

{{< docs/shared lookup="visualizations/multiple-y-axes.md" source="grafana" version="<GRAFANA_VERSION>" leveloffset="+2" >}}

## Configuration options

{{< docs/shared lookup="visualizations/config-options-intro.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Panel options

{{< docs/shared lookup="visualizations/panel-options.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Tooltip options

{{< docs/shared lookup="visualizations/tooltip-options-2.md" source="grafana" version="<GRAFANA_VERSION>" leveloffset="+1">}}

### Legend options

{{< docs/shared lookup="visualizations/legend-options-1.md" source="grafana" version="<GRAFANA_VERSION>" leveloffset="+1" >}}

### Axis options

{{< docs/shared lookup="visualizations/axis-options-1.md" source="grafana" version="<GRAFANA_VERSION>" leveloffset="+1" >}}

### Graph styles options

* goal
  * graph's general appearance
    * EXCEPT [color](#standard-options)

* [here](/grafana/docs/sources/shared/visualizations/graph-styles-options.md)

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
