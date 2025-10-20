---
canonical: https://grafana.com/docs/grafana/latest/alerting/alerting-rules/create-recording-rules/create-data-source-managed-recording-rules/
description: Recording rules allow you to pre-compute expensive queries in advance and save the results as a new set of time series. Data source-managed recording rules can create a recording rule for Prometheus-based data sources like Mimir or Loki.
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
title: Create data source-managed recording rules
weight: 402
refs:
  create-recording-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-recording-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-recording-rules/
---

# Create data source-managed recording rules

* | data source-managed groups,
  * alert rules & recording rules, are evaluated SEQUENTIALLY
    * useful | recording rules
      * Reason:🧠recording rule is evaluated BEFORE any other alert rule🧠

* ways to create
  * -- via -- Grafana UI
  * AUTOMATICALLY | connect data source / has a recording rule

## requirements

- write permission | Prometheus or Loki data source
- | Grafana Mimir and Loki data sources,
  - enable the ruler API -- by configuring their -- respective services
  - **Loki**
    - rule storage types
      - `local`
        - default one
        - supports ⚠️ONLY viewing of rule⚠️
          - if you want to edit rules -> configure other
  - **Mimir**
    - use `/prometheus` prefix
    - [Query API](/docs/mimir/latest/operators-guide/reference-http-api/#querier--query-frontend) & [Ruler API](/docs/mimir/latest/operators-guide/reference-http-api/#ruler) are | SAME URL

## namespace and group

* Namespaces
  * \>= 1 rule groups
  * goal
    * organizational purpose
