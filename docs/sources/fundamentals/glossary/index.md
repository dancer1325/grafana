---
aliases:
  - ../basics/glossary/
  - ../getting-started/glossary/
  - ../guides/glossary/
description: Grafana glossary
keywords:
  - grafana
  - intro
  - glossary
  - dictionary
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Glossary
weight: 850
---

# Glossary

| Term                        | Definition                                                                                                                                                                                                                                                                                                  |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| app plugin                  | == Grafana's extension / provide ADDITIONAL functionality (panel plugin + data source plugins + custom pages)                                                                                                                                                                                               |
| dashboard                   | == set of >=1 related-panels / organized \| rows                                                                                                                                                                                                                                                            |
| data source                 | == file, database, or service / provide the data <br/> types <br/> &nbsp;&nbsp; default <br/> &nbsp;&nbsp; additional -- through -- plugins                                                                                                                                                                 |
| data source plugin          | extends Grafana / support ADDITIONAL data sources                                                                                                                                                                                                                                                           |
| exemplar                    | An exemplar is any data that serves as a detailed example of one of the observations aggregated into a metric. An exemplar contains the observed value together with an optional timestamp and arbitrary labels, which are typically used to reference a trace.                                             |
| Explore                     | allows focus on building a query <br/> used BEFORE building a dashboard <br/> [MORE](https://grafana.com/docs/grafana/latest/explore)                                                                                                                                                                       |
| export or import dashboard  | Grafana includes the ability to export your dashboards to a file containing JSON. Community members sometimes share their created dashboards on the [Grafana Dashboards page](https://grafana.com/grafana/dashboards). Dashboards previously exported or found on this site may be imported by other users. |
| exporter                    | An exporter translates data that comes out of a data source into a format that Prometheus can digest.                                                                                                                                                                                                       |
| Integration (Grafana Cloud) | Each Integration in Grafana Cloud uses the cloud agent to connect your data source to Grafana Cloud for visualizing. Note: Prometheus uses the word "integrations" to refer to software that exposes Prometheus metrics without needing an exporter, which is a different use of the same word we use here. |
| graph                       | A commonly-used visualization that displays data as points, lines, or bars.                                                                                                                                                                                                                                 |
| mixin                       | == Grafana dashboards + Prometheus rules & alerts / written \| Jsonnet & packaged \| bundle                                                                                                                                                                                                                 |
| panel                       | == Grafana's basic building block <br/> == query + visualization                                                                                                                                                                                                                                            |
| panel plugin                | == Grafana's extension / provide ADDITIONAL visualization options                                                                                                                                                                                                                                           |
| plugin                      | == Grafana's extension / provide ADDITIONAL functionality                                                                                                                                                                                                                                                   |
| query                       | request data -- from a -- data source <br/> query language -- depend on the -- specific data source                                                                                                                                                                                                         |
| time series                 | A series of measurements, ordered by time. Time series are stored in data sources and returned as the result of a query.                                                                                                                                                                                    |
| trace                       | An observed execution path of a request through a distributed system. For more information, refer to [What is Distributed Tracing?](https://opentracing.io/docs/overview/what-is-tracing/)                                                                                                                  |
| transformation              | Transformations process the result set of a query before it's passed on for visualization. For more information, refer to the [Transformations overview](https://grafana.com/docs/grafana/latest/panels/transformations) topic.                                                                             |
| visualization               | == graphical representation of query results                                                                                                                                                                                                                                                                |
