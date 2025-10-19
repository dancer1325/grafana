---
aliases:
  - ../fundamentals/alert-rules/recording-rules/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/recording-rules/
  - ../unified-alerting/alerting-rules/create-cortex-loki-managed-recording-rule/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/alerting-rules/create-cortex-loki-managed-recording-rule/
  - ../unified-alerting/alerting-rules/create-mimir-loki-managed-recording-rule/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/alerting-rules/create-mimir-loki-managed-recording-rule/
  - ../alerting-rules/create-mimir-loki-managed-recording-rule/ # /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-mimir-loki-managed-recording-rule/
canonical: https://grafana.com/docs/grafana/latest/alerting/alerting-rules/create-recording-rules/
description: Recording rules allow you to pre-compute frequently needed or computationally expensive expressions and save the results as a new set of time series. Querying precomputed results is faster and can reduce system load.
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
title: Create recording rules
weight: 400
refs:
  grafana-managed-recording-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-recording-rules/create-grafana-managed-recording-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-recording-rules/create-grafana-managed-recording-rules/
  data-source-managed-recording-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-recording-rules/create-data-source-managed-recording-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-recording-rules/create-data-source-managed-recording-rules/
---

# Configure recording rules

* Recording rules
  * allows
    * pre-compute queries + save the results -- as -- NEW time series metrics 
      * NEW time series metrics uses
        * OTHER alert rules
        * OTHER dashboard queries
  * use cases
    * **Faster queries**
    * **Reduce system load:**
      - Reason:🧠Precompute specific queries in advanc🧠
    * **Simplifying complex aggregations:**
      - Reason:🧠use NEW metric🧠
    * **Reusing queries across alerts:**
      - Improve efficiency by reusing the same query across similar alert rules and dashboards
  * types of recording rules
    1. [Grafana-managed recording rules](ref:grafana-managed-recording-rules)
       * ALLOWED | any Grafana data source -- supported by -- alerting
       * recommended
    2. [Data source-managed recording rules](ref:data-source-managed-recording-rules)
       * requirements
         * Prometheus-based data sources (Mimir, Loki or Prometheus)
