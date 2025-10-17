---
aliases:
  - rules/ # /docs/grafana/<GRAFANA_VERSION>/alerting/rules/
  - unified-alerting/alerting-rules/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/alerting-rules/
  - ./create-alerts/ # /docs/grafana/<GRAFANA_VERSION>/alerting/create-alerts/
canonical: https://grafana.com/docs/grafana/latest/alerting/alerting-rules/
description: Configure alert rules
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Configure alert rules
weight: 120
refs:
  alert-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/
  configure-grafana-alerts:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-grafana-managed-rule/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-grafana-managed-rule/
  configure-ds-alerts:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-data-source-managed-rule/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-data-source-managed-rule/
  recording-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-recording-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-recording-rules/
  import-to-grafana-managed:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/alerting-migration/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/alerting-migration/
  comparison-ds-grafana-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-data-source-managed-rule/#comparison-with-grafana-managed-rules
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-data-source-managed-rule/#comparison-with-grafana-managed-rules
---

# Configure alert rules

* [Alert rules](ref:alert-rules)
  * requirements
    * ⚠️compatible Data source⚠️
      * == ❌NOT valid -- with -- Grafana's special built-in data source❌
  * == 👀your alerting system's central component👀
  * == >=1 queries + condition + evaluation period + ADDITIONAL options  
    * querieS
      * select the data to measure
    * evaluation period
      * how often to evaluate the rule  
    * ADDITIONAL options
      * manage 
        * alert events
        * alert notifications
  * supported types 
    * alert rules
      1. **Grafana-managed alert rules**
         * recommended option
           * Reason:🧠offer a [richer feature set](ref:comparison-ds-grafana-rules)🧠
         * query backend data sources 
      1. **Data source-managed alert rules**
         * == 👀alert rules / stored | data source itself👀
         * AVAILABLE | Prometheus-based data sources (Mimir, Loki, and Prometheus) 
         * [can be converted -- into -- Grafana-managed rules](ref:import-to-grafana-managed) 
           * == Grafana Alerting manage them
    * [recording rules](ref:recording-rules)
