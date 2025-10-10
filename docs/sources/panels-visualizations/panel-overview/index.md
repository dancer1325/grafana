---
keywords:
  - transform
  - query
  - panel
  - dashboard
  - rows
  - dynamic
  - add
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Panel overview
title: Panel overview
description: Learn about the features of the panel
weight: 15
refs:
  configure-panel-options:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-panel-options/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-panel-options/
  configure-standard-options:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-standard-options/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-standard-options/
  data-sources:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/connect-externally-hosted/data-sources/
  configure-data-links:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-data-links/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-data-links/
  visualization:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/visualizations/
  legend:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-legend/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-legend/
  create:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-grafana-managed-rule/#create-alerts-from-panels
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-grafana-managed-rule/#create-alerts-from-panels
  share:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/share-query/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/share-query/
  tooltips:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-tooltips/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-tooltips/
  ai:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/manage-dashboards/#set-up-generative-ai-features-for-dashboards
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/dashboards/manage-dashboards/#set-up-generative-ai-features-for-dashboards
  configure-value-mappings:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-value-mappings/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-value-mappings/
  configure-field-overrides:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-overrides/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-overrides/
  query:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/
  panel-links:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/build-dashboards/manage-dashboard-links/#panel-links
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/dashboards/build-dashboards/manage-dashboard-links/#panel-links
  data-source-management:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/data-source-management/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/data-source-management/
  transformations:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/transform-data/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/transform-data/
  configure-thresholds:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-thresholds/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-thresholds/
---

# Panel overview

* Grafana panel
  * == visual representation OF ([query](ref:query) + [visualization](ref:visualization))
  * ALLOWED customizations
    * apply [transformations](ref:transformations)
    * display options
  * | dashboards,
    * can be
      * dragged, 
      * dropped,
      * resize
  * [panel editor](../panel-editor-overview)

## Panel feature overview

![Annotated panel with time series visualization](/grafana/media/docs/panels-visualizations/screenshot-panel-overview-ann-v11.0.png)

1. **Panel title** 
   1. ways to create
      1. manually
      2. -- via -- [generative AI features](ref:ai)
1. **Panel description** 
   1. ways to create
      1. manually
      2. -- via -- [generative AI features](ref:ai)
1. **Links** 
   2. add [panel links](ref:panel-links) -- to -- other dashboards, panels, or external sites
1. **Panel menu** 
   1. allows
      1. access actions -- _Example:_ **View**, **Edit**, **Inspect**, and **Remove** --
1. **Legend**
   2. Change series colors, y-axis, and series visibility directly from the [legend](ref:legend).
1. **Tooltips**
   2. View [tooltips](ref:tooltips) to get more information about data points.

## Panel menu

* valid actions
  - **View**
    - view the panel | full screen
  - **Edit**
    - [panel editor](../panel-editor-overview)
  - **Share**
    - share the panel -- as a -- link, embed, or snapshot
  - **Explore**
    - open the panel | **Explore**,
      - == focus | your query
  - **Inspect**: 
    - [open the **Inspect** drawer](../panel-inspector)
  - **Extensions**
    - requirements
      - app plugins installed / contribute an [extension](https://grafana.com/developers/plugin-tools/key-concepts/ui-extensions) | panel menu 
    - allows
      - accessing other actions / provided -- by -- installed applications
        - _Example:_ declaring an incident
  - **More**: 
    - **Duplicate**
    - **Copy**
      - Copy the panel | clipboard
    - **New library panel**
      - create a panel / can be imported | OTHER dashboards
    - **New alert rule**
      - open the alert rule configuration page | **Alerting** 
        - enable [create a Grafana-managed alert](ref:create) -- based on the -- panel queries
    - **Hide legend**
    - **Get help**
      - Send a snapshot or panel data -- to -- Grafana Labs Technical Support
  - **Remove**: Remove the panel from the dashboard.

![](/grafana/media/docs/panels-visualizations/panelMenu.png)

* _Example:_ [here](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser)

## Keyboard shortcuts | panels

* `?`
  * display ALL AVAILABLE keyboard shortcuts

## Add a panel | Dashboard

* if there is
  * NO visualization, **+ Add visualization**

    ![Empty dashboard state](/grafana/media/docs/panels-visualizations/addPanelEmptyVisualization.png)
  * some visualization
    * **Edit** > **Add** > **Visualization**

   ![Add dropdown](/grafana/media/docs/panels-visualizations/addPanelNoEmpty.png)

## Panel configuration

- [Configure panel options](ref:configure-panel-options)
- [Configure standard options](ref:configure-standard-options)
- [Configure a legend](ref:legend)
- [Configure tooltips](ref:tooltips)
- [Configure data links](ref:configure-data-links)
- [Configure value mappings](ref:configure-value-mappings)
- [Configure thresholds](ref:configure-thresholds)
- [Configure field overrides](ref:configure-field-overrides)
