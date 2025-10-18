---
canonical: https://grafana.com/docs/grafana/latest/alerting/fundamentals/alert-rule-evaluation/evaluation-within-a-group/
description: An alert instance is considered stale when its series disappears for a number of consecutive evaluation intervals. Learn how Grafana resolves them.
keywords:
  - grafana
  - alerting
  - guide
  - state
labels:
  products:
    - cloud
    - enterprise
    - oss
title: How rules are evaluated within a group
menuTitle: Evaluation within a group
weight: 150
refs:
  import-ds-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/alerting-migration/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/alerting-migration/
---

# How rules are evaluated within a group

* rules | 
  * DIFFERENT evaluation groups, 
    * can be evaluated SIMULTANEOUSLY
  * SAME evaluation group,
    * are evaluated -- based on the -- rule type
      - **Grafana-managed** rules
        - CONCURRENTLY | DIFFERENT times
      - **Data source-managed** rules
        - SEQUENTIALLY
        - uses
          - ensure recording rules are evaluated BEFORE alert rules
      - **Grafana-managed rules / [imported -- from -- data source-managed rules](ref:import-ds-rules)**
        - SEQUENTIALLY
