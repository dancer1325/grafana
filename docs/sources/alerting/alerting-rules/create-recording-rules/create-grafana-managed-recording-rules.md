---
canonical: https://grafana.com/docs/grafana/latest/alerting/alerting-rules/create-recording-rules/create-grafana-managed-recording-rules/
description: Recording rules allow you to pre-compute expensive queries in advance and save the results as a new set of time series. Grafana-managed recording rules can create a recording rule for any data source supported by alerting.
keywords:
  - grafana
  - alerting
  - guide
  - rules
  - recording rules
  - configure
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Create Grafana-managed recording rules
weight: 401
refs:
  expressions:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/queries-conditions/#expression-queries
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/queries-conditions/#expression-queries
  create-recording-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-recording-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-recording-rules/
  alerting-data-sources:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-grafana-managed-rule/#supported-data-sources
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-grafana-managed-rule/#supported-data-sources
  configure-grafana-min-interval:
    - pattern: /docs/
      destination: /docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#min_interval
  configure-feature-toggles:
    - pattern: /docs/
      destination: /docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/feature-toggles/
---

# Create Grafana-managed recording rules
* AFTER creating it, available the NEW metric

## requirements

* TSDB (time-series database) | store recording rule results
  * | Grafana cloud,
    * ALREADY included
  * | Grafana OSS & Grafana Enterprise
    * bring your OWN Prometheus-compatible database
    * ⚠️if you do NOT specify a target data source | write the NEW metric -> use Grafana's configuration `recording_rules.default_datasource_uid`⚠️

      ```
      [recording_rules]
      default_datasource_uid = my-uid
      ```
* Prometheus-based data source's CL's flag `web.enable-remote-write-receiver`

## recording rule's restrictions

* NEW metric name MUST follow [Prometheus metric names](https://prometheus.io/docs/concepts/data_model/#metric-names-and-labels)
* | Define recording rule's
  * **Options** dropdown time range
    * fixed relative time ranges
    * NOT support absolute time ranges
