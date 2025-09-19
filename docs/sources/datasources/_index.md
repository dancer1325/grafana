---
aliases:
  - data-sources/
  - overview/
  - ./features/datasources/
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Data sources
weight: 60
refs:
  query-transform-data:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/
  alerts:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/
  grafana-enterprise:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/introduction/grafana-enterprise/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/introduction/grafana-enterprise/
  organization-roles:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/roles-and-permissions/#organization-roles
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/roles-and-permissions/#organization-roles
  explore:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/explore/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/explore/
  data-source-management:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/data-source-management/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/data-source-management/
  plugin-management:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/plugin-management/
    - pattern: /docs/grafana-cloud
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/plugin-management/
  panels:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/
---

# Grafana data sources

* goal
  * how to manage data sources
  * how to configure or query the built-in data sources

* types
  * built-in
    * see list of [datasource plugins](https://grafana.com/grafana/plugins/) 
  * if you need OTHER data sources -> install a data source plugin
    * if the plugin does NOT exist -> develop a custom plugin
      * see [Create a data source plugin](#create-a-data-source-plugin)
* [youtube](https://www.youtube.com/watch?v=cqHO0oYW6Ic)
  * goal
    * add as data sources: Loki, Tempo, Mimir

* OWN _query editor_ / EACH data source
* 👀once you add & configure a data source -> you can use it -- as -- many operations' input 👀
  - Query the data -- via -- [Explore](ref:explore)
  - Visualize | [panels](ref:panels)
  - Create rules -- for -- [alerts](ref:alerts)

## Manage data sources

* TODO:
Only users with the [organization administrator role](ref:organization-roles) can add or remove data sources.
To access data source management tools in Grafana as an administrator, navigate to **Configuration > Data Sources** in the Grafana sidebar.

For details on data source management, including instructions on how configure user permissions for queries, refer to the [administration documentation](ref:data-source-management).

## Add a data source

Before you can create your first dashboard, you need to add your data source.

{{< admonition type="note" >}}
Only users with the organization admin role can add data sources.
{{< /admonition >}}

**To add a data source:**

1. Click **Connections** in the left-side menu.
1. Enter the name of a specific data source in the search dialog. You can filter by **Data source** to only see data sources.
1. Click the data source you want to add.
1. Configure the data source following instructions specific to that data source.

## Use query editors

* uses
  * create queries |
    * [dashboard panels](ref:query-transform-data) or
    * [Explore](ref:explore)

* ⚠️DIFFERENT query language / data source ⚠️
  * -> EACH data source query editor differently
    * looks
      * _Example1:_ provide auto-completion features, metric names, variable suggestions, or a visual query-building interface
      * _Example2:_ [Prometheus query builder](https://vimeo.com/720004179)
    * functions

* see [Query and transform data](ref:query-transform-data)

## Special data sources

### Grafana

* == built-in data source /
  * generates random walk data
    * -> uses
      * testing visualizations
      * running experiments
  * can
    * poll the data source's [Testdata]({{< relref "./testdata/" >}})
    * list files
    * get other data -- from a -- Grafana installation 

### Mixed

* allows
  * run queries | MULTIPLE data sources | SAME panel
    * 1@ query
      * 👀-- uses the -- data source / was selected BEFORE you selected **Mixed** 👀
    * EXISTING query -- can NOT be changed to use the -- **Mixed** data source
* _Example:_ [Mixed Datasources Example](https://play.grafana.org/d/000000100/)

### Dashboard

* == data source / | SAME dashboard, can use 
  * result set -- from -- another panel
  * data -- from -- annotations / attached | selected panel
* _Example:_ [Panel as a Data Source](https://play.grafana.org/d/ede8zps8ndb0gc/)

## Built-in core data sources

* included | Grafana documentation

{{< column-list >}}

- [Alertmanager](alertmanager/)
- [AWS CloudWatch](aws-cloudwatch/)
- [Azure Monitor](azure-monitor/)
- [Elasticsearch](elasticsearch/)
- [Google Cloud Monitoring](google-cloud-monitoring/)
- [Graphite](graphite/)
- [InfluxDB](influxdb/)
- [Jaeger](jaeger/)
- [Loki](loki/)
- [Microsoft SQL Server (MSSQL)](mssql/)
- [MySQL](mysql/)
- [OpenTSDB](opentsdb/)
- [PostgreSQL](postgres/)
- [Prometheus](prometheus/)
- [Pyroscope](pyroscope/)
- [Tempo](tempo/)
- [Testdata](testdata/)
- [Zipkin](zipkin/)

{{< /column-list >}}

## Add additional data source plugins

You can add additional data sources as plugins (that are not available in core Grafana), which you can install or create yourself.

### Find data source plugins in the plugin catalog

To view available data source plugins, go to the [plugin catalog](/grafana/plugins/?type=datasource) and select the "Data sources" filter.
For details about the plugin catalog, refer to [Plugin management](ref:plugin-management).

You can further filter the plugin catalog's results for data sources provided by the Grafana community, Grafana Labs, and partners.
If you use [Grafana Enterprise](ref:grafana-enterprise), you can also filter by Enterprise-supported plugins.

For more documentation on a specific data source plugin's features, including its query language and editor, refer to its plugin catalog page.

### Create a data source plugin

To build your own data source plugin, refer to the [Build a data source plugin](/developers/plugin-tools/tutorials/build-a-data-source-plugin) tutorial and [Plugin tools](/developers/plugin-tools).
