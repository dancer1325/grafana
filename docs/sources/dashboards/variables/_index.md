---
aliases:
  - ../variables/ # /docs/grafana/<GRAFANA VERSION>/variables/
  - ../variables/templates-and-variables/ # /docs/grafana/<GRAFANA VERSION>/variables/templates-and-variables/
  - ../variables/variable-examples/ # /docs/grafana/<GRAFANA VERSION>/variables/variable-examples/
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Variables
description: Add variables to metric queries and panel titles to create interactive and dynamic dashboards
weight: 800
---

# Variables

* variable
  * == placeholder for a value
    * set | top of the dashboard
    
      ![](/grafana/media/docs/dashboards/variablesLocation.png)

  * allows
    * reuse dashboards
      * == interactive dashboards
      * -> simplify maintenance
  * uses
    * change the data displayed | your dashboard 
  * use cases
    * administrators / want to enable Grafana viewers -- to -- adjust visualizations WITHOUT giving FULL editing permissions 
  * settings
    * Dashboard Settings > Variables
  * _Example:_ [Grafana sandbox](https://play.grafana.org/goto/aez99iak7arcwb?orgId=1)

* [Youtube](https://www.youtube.com/watch?v=mMUJ3iwIYwc)

* uses |
  - Data source queries
  - [Panel repeating options](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-panel-options/#configure-repeating-panels)
  - [Dashboard and panel links](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/dashboards/build-dashboards/manage-dashboard-links/)
  - Titles
  - Descriptions
  - [Transformations](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/transform-data/)

## Template variables {#templates}

* _template_
  * == query / contains a variable (`$variableName`)
  * _Example:_ [here](https://play.grafana.org/goto/B9Xog68Hg?orgId=1)
    * | panel, edit,

    ![](/grafana/media/docs/dashboards/templateVariables.png)

### Variables in URLs

* Variable values
  * are synced -- , via [query parameter syntax](variable-syntax/index.md#query-parameters), `var-<varname>=value, to -- URL
    * _Example:_ 
      ```text
      https://play.grafana.org/d/HYaGDGIMk/templating-global-variables-and-interpolation?orgId=1&from=now-6h&to=now&timezone=utc&var-Server=CCC&var-MyCustomDashboardVariable=Hello%20World%21
      # variables
      # 1. `var-Server=CCC`
      # 2. `var-MyCustomDashboardVariable=Hello%20World%21` 
      ```

## Additional examples

- [Templating - Repeated panels](https://play.grafana.org/goto/yfZOReUNR?orgId=1)
  - control NUMBER of panels | dashboard
- [Templating - Nested Variables Drilldown](https://play.grafana.org/d/testdata-nested-variables-drilldown/)
  - change a variable -> change nested variable
- [Templating - Global variables and interpolation](https://play.grafana.org/d/HYaGDGIMk/)
  - how does the Grafana variables syntax works?

