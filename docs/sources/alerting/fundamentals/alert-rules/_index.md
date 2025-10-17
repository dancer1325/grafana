---
aliases:
  - ../fundamentals/data-source-alerting/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/data-source-alerting/
  - ../fundamentals/alert-rules/alert-instances/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/alert-instances/
  - ../fundamentals/alert-rules/organising-alerts/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/organising-alerts/
  - ../fundamentals/alert-rules/alert-rule-types/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/alert-rule-types/
canonical: https://grafana.com/docs/grafana/latest/alerting/fundamentals/alert-rules/
description: Learn about alert rules
keywords:
  - grafana
  - alerting
  - rules
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Alert rules
weight: 100
refs:
  queries-and-conditions:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/queries-conditions/#data-source-queries
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/queries-conditions/#data-source-queries
  alert-condition:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/queries-conditions/#alert-condition
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/queries-conditions/#alert-condition
  alert-rule-evaluation:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/rule-evaluation/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/rule-evaluation/
  notifications:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/
  create-recording-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-recording-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-recording-rules/
  configure-grafana-alerts:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-grafana-managed-rule/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-grafana-managed-rule/
  comparison-ds-grafana-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-data-source-managed-rule/#comparison-with-grafana-managed-rules
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-data-source-managed-rule/#comparison-with-grafana-managed-rules
---

# Alert rules

* alert rule
  * == set of evaluation criteria | alert should fire
  * == 
    * [Queries](ref:queries-and-conditions)
      * == dataset / evaluate
    * [alert condition (threshold)](ref:alert-condition)
      * uses
        * exceed -- to -- trigger the alert instance
    * [alert rule evaluation](ref:alert-rule-evaluation)
    * OTHER options (expressions + labels + annotations + error and no data handling + notification routing)

![](/grafana/media/docs/alerting/alerting-query-conditions-default-options.png)

## Alert rule types

* Grafana Alerting
  * 👀inherits the Prometheus Alerting model👀
  * supported alert rule types
    - **Data source-managed alert rules**
      - requirements
        - query Prometheus-based data sources (Mimir, Loki, Prometheus)
      - stored | data source
      - enable
        - these data sources' horizontal scalability 
    - **Grafana-managed alert rules**
      - 👀recommended one👀
      - support
        - [data sources](/grafana/plugins/data-source-plugins/?features=alerting)
          - MULTIPLE | 1! alert rule
        - expression-based transformations,
        - advanced alert conditions,
        - images | notifications,
        - handling of error & NOT data states
        - [MORE](ref:comparison-ds-grafana-rules)
  * [how to configure](ref:configure-grafana-alerts)

## Recording rules

* evaluated periodically
* uses |
  * frequently used OR computationally expensive queries
* how does it work?
  * pre-computes the queries
  * saves the results -- as a -- NEW time series metric /
    * NEW recording metric can be used | 
      * alert rules
      * dashboards
