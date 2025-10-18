---
aliases:
  - ../unified-alerting/alerting-rules/create-mimir-loki-managed-rule/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/alerting-rules/create-mimir-loki-managed-rule/
  - ../unified-alerting/alerting-rules/edit-cortex-loki-namespace-group/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/alerting-rules/edit-cortex-loki-namespace-group/
  - ../unified-alerting/alerting-rules/edit-mimir-loki-namespace-group/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/alerting-rules/edit-mimir-loki-namespace-group/
  - ../alerting-rules/create-mimir-loki-managed-rule/ # /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-mimir-loki-managed-rule/
canonical: https://grafana.com/docs/grafana/latest/alerting/alerting-rules/create-data-source-managed-rule/
description: Configure data source-managed alert rules alert for an external Grafana Mimir or Loki instance
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
title: Configure data source-managed alert rules
weight: 400
refs:
  configure-prometheus-data-source-alerting:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/prometheus/configure/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/connect-externally-hosted/data-sources/prometheus/configure/
  configure-grafana-managed-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-grafana-managed-rule/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-grafana-managed-rule/
  supported-data-sources-grafana-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-grafana-managed-rule/#supported-data-sources
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-grafana-managed-rule/#supported-data-sources
  notification-policies:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/notification-policies/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/notification-policies/
  pending-period:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rule-evaluation/#pending-period
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rule-evaluation/#pending-period
  alert-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/
  alert-rule-labels:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/annotation-label/#labels
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/annotation-label/#labels
  alert-rule-evaluation:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rule-evaluation/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rule-evaluation/
  shared-provision-alerting-resources:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/set-up/provision-alerting-resources/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/set-up/provision-alerting-resources/
  shared-alert-rule-template:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/templates/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/templates/
  shared-annotations:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/annotation-label/#annotations
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/annotation-label/#annotations
  shared-link-alert-rules-to-panels:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/link-alert-rules-to-panels/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/link-alert-rules-to-panels/
  import-to-grafana-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/alerting-migration/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/alerting-migration/
  create-recording-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-recording-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-recording-rules/
  rbac:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/set-up/configure-rbac/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/set-up/configure-rbac/
  expression-queries:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/queries-conditions/#advanced-options-expressions
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/queries-conditions/#advanced-options-expressions
  alert-condition:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/queries-conditions/#alert-condition
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/queries-conditions/#alert-condition
  notification-images:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/template-notifications/images-in-notifications/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/template-notifications/images-in-notifications/
  view-alert-state-history:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/monitor-status/view-alert-state-history/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting/monitor-status/view-alert-state-history/
  view-compare-and-restore-alert-rules-versions:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/monitor-status/view-alert-rules/#view-compare-and-restore-alert-rules-versions
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting/monitor-status/view-alert-rules/#view-compare-and-restore-alert-rules-versions
  th-provisioning:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/set-up/provision-alerting-resources/terraform-provisioning/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/set-up/provision-alerting-resources/terraform-provisioning/
  no-data-error-states:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rule-evaluation/nodata-and-error-states/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rule-evaluation/nodata-and-error-states/
  stale-alert-instances:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rule-evaluation/stale-alert-instances/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rule-evaluation/stale-alert-instances/
---

# Configure data source-managed alert rules

* | Grafana Alerting, you can
  1. about Grafana Mimir's alert rules & Grafana Loki's alert rules,
     1. create
     2. edit 
  1. about Prometheus data sources,
     * if ["Manage alerts via Alerting UI" is enabled](ref:configure-prometheus-data-source-alerting) -> view rules  
     * ❌NOT possible to create or edit them❌
  1. [import Loki, Mimir, and Prometheus data source-managed rules](ref:import-to-grafana-rules) -- into -- Grafana-managed rules

* if you use MULTIPLE Grafana instances & data source-managed alert rules
  * pros
    * | evaluate rules, load balancing
  * cons
    * operations complexity
      * _Example:_ SAME rule is NOT evaluated | DIFFERENT Grafana instances

## Grafana-managed rules vs data source-managed alert rules

| Feature                                                                                                        | Grafana-managed alert rule                      | Data source-managed alert rule                           |
|----------------------------------------------------------------------------------------------------------------|-------------------------------------------------| --------------------------------------------------------------------------------- |
| supported data sources -- configured via -- [`alerting` option](ref:rbac)                                      | enabled for ALL                                 | Mimir and Loki data sources                      |
| Mix and match data sources                                                                                     | Yes                                             | No                                                                                |
| [expressions](ref:expression-queries) allows transform your data & set [alert conditions](ref:alert-condition) | Yes                                             | No                                                                                |
| [No data and error states](ref:no-data-error-states)                                                           | Yes                                             | No                                                                                |
| [Stale alert instances](ref:stale-alert-instances)                                                             | Yes                                             | No                                                                                |
| [Images in alert notifications](ref:notification-images)                                                       | Yes                                             | No                                                                                |
| [Role-based access control](ref:rbac)                                                                          | Yes                                             | No                                                                                |
| [Alert state history](ref:view-alert-state-history)                                                            | Yes                                             | No                                                                                |
| [Alert version history](ref:view-compare-and-restore-alert-rules-versions)                                     | Yes                                             | No                                                                                |
| [Terraform provisioning](ref:th-provisioning)                                                                  | Yes                                             | No                                                                                |
| [Recording rules](ref:create-recording-rules)                                                                  | Yes                                             | Yes                                                                               |
| Organization                                                                                                   | Organize and manage access with folders         | Use namespaces                                                                    |
| Alert rule evaluation                                                                                          | Alert evaluation is done in Grafana             | Alert rule evaluation is done in the data source and allow for horizontal scaling |
| Scaling                                                                                                        | Alert rules are stored in the Grafana database. | Alert rules are stored within the data source and allow for horizontal scaling    |

## Create data source-managed alert rules

### requirements

* write permission -- to the -- Mimir OR Loki data source

#### Enable the Ruler API

[Mimir Ruler API](/docs/mimir/latest/references/http-api/#ruler) or [Loki Ruler API](/docs/loki/latest/api/#ruler)

- **Mimir** 
  - use the `/prometheus` prefix
  - The Prometheus data source supports both Grafana Mimir and Prometheus, and Grafana expects that both the [Query API](/docs/mimir/latest/operators-guide/reference-http-api/#querier--query-frontend) and [Ruler API](/docs/mimir/latest/operators-guide/reference-http-api/#ruler) are under the same URL
  - You cannot provide a separate URL for the Ruler API.

- **Loki** 
  - The `local` rule storage type, default for the Loki data source, supports only viewing of rules
  - To edit rules, configure one of the other rule storage types.

#### Permissions

Alert rules for Mimir or Loki instances can be edited or deleted by users with **Editor** or **Admin** roles.

If you do not want to manage alert rules for a particular data source, 
go to its settings and clear the **Manage alerts via Alerting UI** checkbox.

#### Provisioning

Note that if you delete an alert resource created in the UI, you can no longer retrieve it.

To backup and manage alert rules, you can [provision alerting resources](ref:shared-provision-alerting-resources) using options such as configuration files, Terraform, or the Alerting API.

[//]: <> ({{< docs/shared lookup="alerts/configure-provisioning-before-begin.md" source="grafana" version="<GRAFANA_VERSION>" >}})

### Set alert rule name

{{< docs/shared lookup="alerts/configure-alert-rule-name.md" source="grafana" version="<GRAFANA_VERSION>" >}}

### Define query and condition

Define a query to get the data you want to measure and a condition that needs to be met before an alert rule fires.

{{< admonition type="note" >}}
By default, new alert rules are Grafana-managed. To switch to **Data source-managed**, follow these instructions.
{{< /admonition >}}

1. Select a Prometheus-based data source from the drop-down list.

   You can also click **Open advanced data source picker** to find more options.

1. Enter a PromQL or LogQL query, including the alert condition.
1. In the **Rule type** option, select **Data source-managed**.
1. Click **Preview alerts**.

### Set alert evaluation behavior

Use [alert rule evaluation](ref:alert-rule-evaluation) to determine how frequently an alert rule should be evaluated and how quickly it should change its state.

1. Select a namespace or click **+ New namespace**.
1. Select an evaluation group or click **+ New evaluation group**.

   If you are creating a new evaluation group, specify the interval for the group.

   All rules within the same group are evaluated sequentially over the same time interval. 
   You can reorder them from the **Alert rules** page.

1. Enter a pending period.

   The [pending period](ref:pending-period) is the period in which an alert rule can be in breach of the condition until it fires.

   Once a condition is met, the alert goes into the **Pending** state. 
   If the condition remains active for the duration specified, the alert transitions to the **Firing** state, else it reverts to the **Normal** state.

### Configure labels and notifications

Add [labels](ref:alert-rule-labels) to your alert rules to set which [notification policy](ref:notification-policies) should handle your firing alert instances.

All alert rules and instances, irrespective of their labels, match the default notification policy. 
If there are no nested policies, or no nested policies match the labels in the alert rule or alert instance, 
then the default notification policy is the matching policy.

1. Add labels if you want to change the way your notifications are routed.

   Add custom labels by selecting existing key-value pairs from the drop down, or add new labels by entering the new key or value.

### Configure notification message

Use [annotations](ref:shared-annotations) to add information to alert messages that can help respond to the alert.

Annotations are included by default in notification messages, and can use text or [templates](ref:shared-alert-rule-template) to display dynamic data from queries.

Grafana provides several optional annotations.

1. Optional: Add a summary.

   Short summary of what happened and why.

1. Optional: Add a description.

   Description of what the alert rule does.

1. Optional: Add a Runbook URL.

   Webpage where you keep your runbook for the alert

1. Optional: Add a custom annotation.

   Add any additional information that could help address the alert.

1. Optional: **Link dashboard and panel**.

   [Link the alert rule to a panel](ref:shared-link-alert-rules-to-panels) to facilitate alert investigation.

1. Click **Save rule**.

[//]: <> ({{< docs/shared lookup="alerts/configure-notification-message.md" source="grafana" version="<GRAFANA_VERSION>" >}})
