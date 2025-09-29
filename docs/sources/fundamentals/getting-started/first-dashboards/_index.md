---
aliases:
  - ../../guides/getting_started/ # /docs/grafana/latest/guides/getting_started/
  - ../../guides/gettingstarted/ # /docs/grafana/latest/guides/gettingstarted/
  - ../../getting-started/build-first-dashboard/ # /docs/grafana/latest/getting-started/build-first-dashboard/
description: Learn how to get started with Grafana by adding a preconfigured dashboard.
labels:
  products:
    - enterprise
    - oss
title: Build your first dashboard
weight: 200
---

# Build your first dashboard

* goal
  * build your first dashboard -- via -- the built-in `Grafana` data source
  * [introduction](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/introduction/)

* ways
  * [self-hosted Grafana](/docs/grafana/latest/installation/docker/)
  * [Grafana Cloud](https://grafana.com/products/cloud/)

* `docker run -d -p 3000:3000 grafana/grafana`

#### Create a dashboard

* * http://localhost:3000/
* admin / admin
* **Dashboards** > **New** > **Add visualization** > 
  * built-in `-- Grafana --` data source
  * **Refresh**
  * **Save dashboard**

#### Next steps

- [create a dashboard](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/dashboards/build-dashboards/create-dashboard/)
- [query](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/#add-a-query)
- [Panels and visualizations](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/panels-visualizations/)
- [Dashboards](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/dashboards/)
- [Keyboard shortcuts](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/dashboards/use-dashboards/#keyboard-shortcuts)
