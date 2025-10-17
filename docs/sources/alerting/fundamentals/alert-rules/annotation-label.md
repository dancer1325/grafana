---
aliases:
  - ../../fundamentals/annotation-label/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/annotation-label/
  - ../../fundamentals/annotation-label/labels-and-label-matchers/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/annotation-label/labels-and-label-matchers/
  - ../../fundamentals/annotation-label/how-to-use-labels/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/annotation-label/how-to-use-labels/
  - ../../alerting-rules/alert-annotation-label/ # /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/alert-annotation-label/
  - ../../unified-alerting/alerting-rules/alert-annotation-label/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/alerting-rules/alert-annotation-label/
canonical: https://grafana.com/docs/grafana/latest/alerting/fundamentals/alert-rules/annotation-label/
description: Learn how to use annotations and labels to store key information about alerts
keywords:
  - grafana
  - alerting
  - guide
  - rules
  - create
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Labels and annotations
weight: 105
refs:
  alert-instances:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals#alert-instances
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals#alert-instances
  link-alert-rules-to-panels:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/link-alert-rules-to-panels/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/link-alert-rules-to-panels/
  templates:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/templates/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/templates/
  alert-rule-evaluation:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rule-evaluation/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rule-evaluation/
  silences:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/create-silence/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/create-silence/
  notification-policies:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/notification-policies/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/notification-policies/
---

# Labels and annotations

* Labels & annotations
  * add alert´s ADDITIONAL information -- via -- key/value pairs

- [Labels](#labels)
  - 💡[alert instance](ref:alert-instances)'s unique identifiers💡 
  - uses
    - differentiate alertS
    - how to manage (search, silence, route) the alerts
- [Annotations](#annotations)
  - provide
    - extra details -- for -- alert responders to help them understand and address potential issues

## Labels

* ALLOWED
  * 👀\>=1 label / EACH alert rule👀
    * 👀if 1 label is DIFFERENT -> DIFFERENT alert instances👀

* label set
  * == alert rule's ALL set of labels

![](/grafana/media/docs/alerting/unified)

- The alerting UI shows labels for every alert instance generated during evaluation of that rule.
- [Notification policies](ref:notification-policies) & [silences](ref:silences)
  - use labels -- to -- 
    - match alert instances
    - route alert instances -- to -- contact points
    - stop their notifications

- Contact points
  - can include labels' information | notification messages

### Label types

#### **User-configured labels**

* _Example:_ `severity`, `priority`, `team`, and `service`

* ways to add
  * manually
  * [templated](ref:templates)
    * generate dynamic values -- from -- query data

#### **Query labels**

* returned -- by the -- data source query
* allows
  * generating MULTIPLE alert instances / SAME alert rule

#### **Reserved labels**

* AUTOMATICALLY added -- by -- Grafana
* are
  - `alertname`
    - alert rule name 
  - `grafana_` 
    - special use 
    - if you want to disable reserved labels -> [`unified_alerting.reserved_labels`](/docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana#unified_alertingreserved_labels)
    - `grafana_folder`
      - folder name / contain the alert

{{<admonition type="note">}}

Two alert rules cannot produce alert instances with the same labels
* If two alert rules have the same labels such as `foo=bar,bar=baz` and `foo=bar,bar=baz` then one of the generated alert instances is discarded.

Ensure the label set for an alert does not have two or more labels with the same name.

- If a configured label has the same name as a data source query label, it replaces the data source label.
- If a configured label has the same name as a reserved label, it is omitted.
  {{</admonition>}}

{{< collapse title="Label key format" >}}

Grafana has a built-in Alertmanager that supports both Unicode label keys and values
* If you are using an external Prometheus Alertmanager, label keys must be compatible with their [data model](https://prometheus.io/docs/concepts/data_model/#metric-names-and-labels).
This means that label keys must only contain _ASCII letters_, _numbers_, and _underscores_.
Label keys must also be matched by the regular expression `[a-zA-Z_][a-zA-Z0-9_]*`.
Any invalid characters are removed or replaced by the Grafana alerting engine before being sent to the external Alertmanager according to the following rules:

- Whitespace is removed.
- ASCII characters are replaced with `_`.
- All other characters are replaced with their lower-case hex representation.
  If this is the first character it's prefixed with `_`.

Example: A label key/value pair `Alert! 🔔="🔥"` will become `Alert_0x1f514="🔥"`.

If multiple label keys are sanitized to the same value, the duplicates have a short hash of the original label appended as a suffix.

{{< /collapse >}}

## Annotations

{{< shared id="annotations-basics" >}}

Annotations add additional information to alert instances, helping responders identify and address potential issues.

Create clear and self-explanatory annotations so that first responders can investigate without needing deeper knowledge of the alert setup.

Annotations are displayed in Grafana and are included by default in notifications. Grafana provides several optional annotations that you can edit:

- `summary`: A short summary of what the alert has detected and why.
- `description`: A detailed description of what happened and what the alert does.
- `runbook_url`: The runbook page to guide operators managing a potential incident.
- `__dashboardUid__` and `__panelId__`: [Link the alert to a dashboard and panel](ref:link-alert-rules-to-panels) to facilitate alert investigation.

{{< /shared >}}

For example, you can edit the annotation `summary` to explain why the alert was triggered:

```
CPU usage has exceeded 80% for the last 5 minutes.
```

And edit the `description` annotation to provide more context and how to respond:

```
The web server's CPU has exceeded 80% for more than 5 minutes.

This indicates that the system is under heavy load and may result in an outage.

Consider scaling the server's resources and investigating bottlenecks.
```

Like labels, annotations can use a [template](ref:templates) to include dynamic data from queries.
