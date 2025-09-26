---
aliases:
  - dashboards/configure-panels-visualizations/
  - features/panels/panels/
  - panels/
keywords:
  - grafana
  - configure
  - panels
  - visualizations
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Panels and visualizations
title: Panels and visualizations
description: Learn about and configure panels and visualizations
weight: 80
hero:
  title: Panels and visualizations
  level: 1
  width: 110
  height: 110
  description: >-
    Easily collect, correlate, and visualize data so you can make informed decisions in real time.
cards:
  title_class: pt-0 lh-1
  items:
    - title: Visualizations
      href: ./visualizations/
      description: Learn about all the visualizations available in Grafana, including which visualizations are ideal for different datasets and how to configure their options.
      height: 24
    - title: Panel overview
      href: ./panel-overview/
      description: Learn about the features of the panel.
      height: 24
    - title: Panel editor
      href: ./panel-editor-overview/
      description: Learn about the features of the panel editor and how to begin editing a panel.
      height: 24
    - title: Configure standard options
      href: ./configure-standard-options/
      description: Learn about configuring standard options like units, field display names, and colors.
      height: 24
    - title: Query and transform data
      href: ./query-transform-data/
      description: Learn about querying and transforming your data to refine your visualizations.
      height: 24
refs:
  query:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/
---

## Overview

* Panels
  * 👀== BASIC building block | Grafana dashboards👀 /
    * variety of 
      * formatting options
      * styling options 
  * 👀== [query](ref:query) + visualization 👀
    * visualization
      * == graphical representation of query results /
        * include options-specific -- to control -- how to display your data  
      * provide
        * DIFFERENT ways to present your data | panel
          * -- depend on -- what best suits the data & your needs
          * _Example:_ time series graphs, heatmaps, cutting-edge 3D charts
  * uses
    * get the information -- to optimize -- performance
  * -- communicate, via queries, with -- data sources

# _Example:_ 
* Grafana cloud

  ![](static/panel.gif)

