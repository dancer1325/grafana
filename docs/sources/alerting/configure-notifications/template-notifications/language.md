---
aliases:
  - ../../manage-notifications/template-notifications/using-go-templating-language/ # /docs/grafana/<GRAFANA_VERSION>/alerting/manage-notifications/template-notifications/using-go-templating-language/
  - ../../configure-notifications/template-notifications/using-go-templating-language/ # /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/template-notifications/using-go-templating-language/
weight: 104
canonical: https://grafana.com/docs/grafana/latest/alerting/configure-notifications/template-notifications/language/
description: Use Go template language to create your notification and alert rule templates
keywords:
  - grafana
  - alerting
  - templates
  - write templates
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Alerting template language
menuTitle: Template language
refs:
  alert-rule-template-reference:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/templates/reference/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/templates/reference/
  alert-rule-template-reference-variables:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/templates/reference/#variables
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/templates/reference/#variables
  notification-template-reference:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/template-notifications/reference/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/template-notifications/reference/
  reference-notificationdata:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/template-notifications/reference/#notification-data
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/template-notifications/reference/#notification-data
---

# Alerting template language

* goal
  * [Go text/template](https://pkg.go.dev/text/template)'s functions & operators / AVAILABLE |
    * notification templates
    * alert rule templates

* Notification templates & alert rule templates (_Examples:_annotations and labels)
  * 💡use Go text/template💡 
    * ❌NOT ALL variables OR functions VALID for notification OR alert rule templates❌ 

## Print

* `{{ somethingToPrint }}`
  * `somethingToPrint` ALLOWED
    * [variable](#variables)'s
      * value
      * field
    * function's result
    * value of dot

    ```
    {{ $values }}
    {{ $values.A.Value }}
    {{ humanize 1000.0 }}
    {{ .Alerts }}
    ```

## Dot -- `.` --

* == special cursor | `text/template`
* == variable / 
  * 👀's value -- depend on -- template's place | use👀
    * [Notification Data](ref:reference-notificationdata) -- notification templates start -- 

      ```
      {{ .Alerts }}
      ```

In annotation and label templates, dot (`.`) is initialized with all alert data
* It’s recommended to use the [`$labels` and `$values` variables](ref:alert-rule-template-reference-variables) instead to directly access the alert labels and query values.

{{< admonition type="note" >}}
Dot (`.`) might refer to something else when used in a [range](#range), a [with](#with), or when writing [templates](#templates) used in other templates.
{{< /admonition >}}

[//]: <> (The above section is not included in the shared file because `refs` links are not supported in shared files.)

{{< docs/shared lookup="alerts/template-language.md" source="grafana" version="<GRAFANA_VERSION>" >}}
