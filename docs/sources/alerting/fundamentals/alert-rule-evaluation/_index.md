---
aliases:
  - ../fundamentals/alert-rules/rule-evaluation/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/rule-evaluation/
canonical: https://grafana.com/docs/grafana/latest/alerting/fundamentals/alert-rule-evaluation/
description: Use alert rule evaluation to determine how frequently an alert rule should be evaluated and how quickly it should change its state
keywords:
  - grafana
  - alerting
  - evaluation
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Alert rule evaluation
weight: 108
refs:
  evaluation-within-a-group:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rule-evaluation/evaluation-within-a-group/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rule-evaluation/evaluation-within-a-group/
  nodata-and-error-states:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rule-evaluation/nodata-and-error-states/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rule-evaluation/nodata-and-error-states/
  import-ds-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/alerting-migration/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/alerting-migration/
  notifications:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/
---

# Alert rule evaluation

* == criteria / fires the alert
  - [Evaluation group](#evaluation-group)
    - == FREQUENCY / alert rule is evaluated
  - [Pending period](#pending-period)
    - == how long the condition MUST be met / start firing
  - [Keep firing for](#pending-period)
    - == AFTER the condition is NO longer met, 
      - how long the alert continues to fire 

  ![](/grafana/media/docs/alerting/alert-rule-evaluation-2.png)

## Alerting lifecycle

* 1 alert rule can generate >= 1 alert instances—one /
  * 1 / EACH series OR dimension produced -- by the -- rule's query
  * alert instance1's state (may be) != alert instance2's state

| Alert instance transiction's state | Description                                                                                                                                   |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| **Normal**                         | == alert's state \| condition (threshold) is NOT met                                                                                          |
| **Pending**                        | == alert's state / threshold has been breached BUT < [pending period](#pending-period)                                                        |
| **Alerting**                       | == alert's state / threshold has been breached > [pending period](#pending-period) <br/> 👀notification is triggered 👀                       |
| **Recovering**                     | == firing alert's state <br/> &nbsp;&nbsp; \| threshold is NO longer breached <br/> &nbsp;&nbsp; < [keep firing for](#keep-firing-for) period |

![](/grafana/media/docs/alerting/alert-rule-evaluation-basic-statediagram.png)

* if an alert rule changes (EXCEPT FOR: updates to annotations, evaluation interval, OR OTHER internal fields) -> its alert instances 
  * 👀reset -- to the -- **NORMAL** state👀
  * update accordingly

## Notification routing

* 👀use cases | alert instances are routed -- for -- [notifications](ref:notifications)👀
  1. transition -- to the -- **Alerting** state
  2. transition -- to -- **Normal** state & marked as `Resolved`

## Evaluation group

* 👀EVERY alert rule & recording rule is assigned -- to an -- evaluation group👀

* Evaluation interval
  * == how frequently the alert rule is checked
  * EXIST / EACH evaluation group

* ways to evaluate the rules
  * concurrently OR
  * sequentially

## Pending period

* **Pending period**
  * == how long the condition MUST be met -- to -- trigger the alert rule
  * 👀prevent unnecessary notifications / caused -- by -- temporary issues👀
  * requirements
    * ⚠️\> evaluation interval⚠️

* Pending state
  * requirements
    * alert condition is met
  * if you set **Pending period=0** -> skip the **Pending** state
    * == transition DIRECTLY -- to -- **Alerting** immediately

- **Normal** -> **Pending** -> **Alerting**

## Keep firing for

* **Keep firing for** period
  * 👀avoid repeated firing-resolving-firing notifications / caused -- by -- flapping conditions 👀
  * AFTER **Keep firing for** period WITHOUT meeting alert rule's condition -> alert transitions -- to the -- **Normal** state & marked as **Resolved**
  * if **Keep firing for** period == 0 -> transition -- DIRECTLY to -- Normal
    * == skip the **Recovering** state 

- **Alerting** → **Recovering** → **Normal (Resolved)**
