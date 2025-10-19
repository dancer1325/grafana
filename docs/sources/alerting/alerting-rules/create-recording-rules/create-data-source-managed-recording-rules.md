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

## Add new recording rule

To create a new data source-managed recording rule:

1. Click **Alerts & IRM** -> **Alerting** -> **Alert rules**.
1. At the top of the Alert rules page, click **More** -> **New Grafana recording rule**.

## Enter recording rule name

The recording rule name must be a Prometheus metric name and contain no whitespace.

## Define recording rule

Select your data source and enter a quer
The queries used in data source-managed recording rules always run as instant queries.

## Add namespace and group

1. From the **Namespace** dropdown, select an existing rule namespace or add a new one.

   Namespaces can contain one or more rule groups and only have an organizational purpose.

1. From the **Group** dropdown, select an existing group within the selected namespace or add a new one.

   Rules within a group are run sequentially at a regular interval, with the same evaluation time.

   Newly created rules are appended to the end of the group, and you can reorder them from the **Alert rules** page.

## Add labels

Optionally, you can add custom labels to the resulting metric by selecting existing key-value pairs from the drop down or entering the new key or value.

## Query the new metric in dashboards or alert rules

Click **Save rule** or **Save rule and exit** to save the rule.

Once saved, the new recording metric is available for use in dashboards and alert rules.
