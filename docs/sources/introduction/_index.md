---
aliases:
  - guides/what-is-grafana/
  - oss-details/
description: Learn about Grafana OSS, Grafana Enterprise, and Grafana Cloud.
labels:
  products:
    - cloud
    - enterprise
    - oss
title: About Grafana
weight: 5
---

# About Grafana
* Grafana open source (OSS)
  * enables you,
    * about metrics + logs + traces,
      * query,
      * visualize,
      * alert on,
      * explore
    * connect OTHER data sources 
      * _Example:_ NoSQL/SQL databases
    * ticketing tools
      * _Example:_ Jira or ServiceNow 
  * provides
    * tools /
      * your time-series database (TSDB) data are turned -- into -- insightful graphs & visualizations

* see 
  * [installed Grafana](../setup-grafana/installation)
  * [playlist](../dashboards/create-manage-playlists)
  * if you are the admin for an enterprise & manage Grafana | MULTIPLE teams,
    * [provisioning](../administration/provisioning)
    * [authentication](../setup-grafana/configure-security/configure-authentication)
  * [Grafana Community forums](https://community.grafana.com/)

## Explore metrics, logs, and traces

* Explore your data
  * -- through -- 
    * ad-hoc queries
    * dynamic drilldown
  * if you want to split view & compare different time ranges, queries and data sources -> see [Explore](../explore)

## Alerts

* alert notifiers
  * built-in PagerDuty, SMS, email, VictorOps, OpsGenie, or Slack

* Alert hooks
  * allow you to
    * create DIFFERENT notifiers -- via -- low-code

## Annotations

* == annotate graphs -- with -- 👀DIFFERENT data sources' rich events👀
  * == correlate data

* == graph marker | Grafana
* ways to create
  * manually | pannel
  * query annotations

* [Annotations](../dashboards/build-dashboards/annotate-visualizations/)

## Dashboard variables

* [Template variables](../dashboards/variables/)
  * allow you to 
    * create dashboards / can be reused
    * drill down | your data

## Configure Grafana

* see
  * [Grafana configuration options](../setup-grafana/configure-grafana/)
  * [Grafana CLI](../cli/)

* == config files + environment variables
  * _Examples:_ default ports, logging levels, email IP addresses, security, ...

## Import dashboards and plugins

* [dashboards](/grafana/dashboards)
* [plugins](https://grafana.com/docs/plugins/)

## Authentication

* supported authentication methods
  * LDAP
  * OAuth

* see [User authentication overview](../setup-grafana/configure-security/configure-authentication/)

* | Grafana
  * OSS
    * users are mapped -- to -- organizations
  * [Enterprise](grafana-enterprise.md)
    * users are mapped -- to -- organizations & teams
    * teams are mapped -- to -- teams

## Provisioning

* allows
  * configure Grafana AUTOMATICALLY
    * == -- via -- script
* uses
  * create MANY dashboards

* [MORE](../administration/provisioning/)

## Permissions

* use case
  * organizations / have 1 Grafana & MULTIPLE teams /
    * keep things separate
    * share dashboards

* | [Grafana Enterprise](grafana-enterprise),
  * create a team of users / set permissions | 
    * [folders & dashboards](../administration/user-management/manage-dashboard-permissions/)
    * [data sources](../administration/data-source-management/#data-source-permissions) 

## Other Grafana Labs OSS Projects

* **Grafana Loki:**
  * Grafana Loki is an open source, set of components that can be composed into a fully featured logging stack
  * [documentation](/docs/loki/latest/).

* **Grafana Tempo:**
  * Grafana Tempo is an open source, easy-to-use and high-volume distributed tracing backend
  * [documentation](/docs/tempo/latest/?pg=oss-tempo&plcmt=hero-txt/).

**Grafana Mimir:** Grafana Mimir is an open source software project that provides a scalable long-term storage for Prometheus
* For more information about Grafana Mimir, refer to [Grafana Mimir documentation](/docs/mimir/latest/).

**Grafana Pyroscope:** Grafana Pyroscope is an open source software project for aggregating continuous profiling data
* Continuous profiling is an observability signal that allows you to understand your workload's resources (CPU, memory, for example) usage down to the line number
* For more information about Grafana Pyroscope, refer to [Grafana Pyroscope documentation](/docs/pyroscope/latest/).

**Grafana Faro:** Grafana Faro is an open source JavaScript agent that embeds in web applications to collect real user monitoring (RUM) data: performance metrics, logs, exceptions, events, and traces
* For more information about using Grafana Faro, refer to [Grafana Faro documentation](/docs/grafana-cloud/monitor-applications/frontend-observability/faro-web-sdk/).

**Grafana Beyla:** Grafana Beyla is an eBPF-based application auto-instrumentation tool for application observability
* eBPF is used to automatically inspect application executables and the OS networking layer as well as capture basic trace spans related to web transactions and Rate-Errors-Duration (RED) metrics for Linux HTTP/S and gRPC services
* All data capture occurs without any modifications to application code or configuration. For more information about Grafana Beyla, refer to [Grafana Beyla documentation](/docs/beyla/latest/).

**Grafana Alloy:** Grafana Alloy is a flexible, high performance, vendor-neutral distribution of the [OpenTelemetry](https://opentelemetry.io/) (OTel) Collector.
It's fully compatible with the most popular open source observability standards such as OpenTelemetry (OTel) and Prometheus.
For more information about Grafana Alloy, refer to the [Grafana Alloy documentation](https://grafana.com/docs/alloy/latest/).

**Grafana k6:** Grafana k6 is an open-source load testing tool that makes performance testing easy and productive for engineering teams. For more information about Grafana k6, refer to [Grafana k6 documentation](/docs/k6/latest/).

**Grafana OnCall:** Grafana OnCall is an open source incident response management tool built to help teams improve their collaboration and resolve incidents faster. For more information about Grafana OnCall, refer to [Grafana OnCall documentation](/docs/oncall/latest/).
