---
aliases:
  - ../manage-notifications/template-notifications/ # /docs/grafana/<GRAFANA_VERSION>/alerting/manage-notifications/template-notifications/
canonical: https://grafana.com/docs/grafana/latest/alerting/configure-notifications/template-notifications/
description: Customize your notifications using notification templates
keywords:
  - grafana
  - alerting
  - notifications
  - templates
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Template notifications
weight: 450
refs:
  template-annotations-and-labels:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/templates/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/templates/
  manage-notification-templates:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/template-notifications/manage-notification-templates/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/template-notifications/manage-notification-templates/
  reference:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/template-notifications/reference/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/template-notifications/reference/
  examples:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/template-notifications/examples/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/template-notifications/examples/
---

# Template notifications

* allows
  * changing the notifications
    * title,
    * message,
    * format 
      * restrictions == ❌NOT possible to modify❌ 
        * the visual appearance
          * _Example:_ add HTML OR CSS
        * the notification integration message service's (slack, team, ...) design 
        * the template's input
        * webhooks' HTTP headers

* built-in templates
  * display COMMON alert details 
  * are
    * `default.title`
      * == **default template** -- for -- notification titles
    * `default.message`
      * == default template -- for -- notification messages

* custom notification template
  * created | notification template group
  * 's name
    * ⚠️MUST be UNIQUE ACROSS ALL notification template groups⚠️
      * recommendations
        * avoid using built-in templates names 
          * _Examples:_ `__subject`, `__text_values_list`, `__text_alert_list`, `default.title` and `default.message`
  * 👀syntax👀
    ```text,title=textWithGoTemplate
    {{define "<NAME>"}}
    ...
    {{end}}
    ```
    * if you do NOT add specifically
      * `{{define "<NAME>"}}` -> added AUTOMATICALLY `{{ define "<NOTIFICATION_TEMPLATE_NAME>" }}`
      * `{{ end }}` -> added AUTOMATICALLY

* notification template group
  * allows
    * test & implement MULTIPLE templates TOGETHER
  * syntax
    ```text,title=textWithGoTemplate
    {{define "<TEMPLATE_1_NAME>"}}
    ...
    {{end}}
    {{define "<TEMPLATE_2_NAME>"}}
    ...
    {{end}}
    ...
    ```

* _[Examples](ref:examples)_

* recommendations
  * ❌NOT add alert instances' extra information | notification templates❌
    * Reason:🧠[use annotations or labels](ref:template-annotations-and-labels) 🧠

## Select a notification template for a contact point

* uses
  * 👀can be ACROSS MULTIPLE contact points👀
    * == ❌NOT tied -- to -- specific contact point integrations❌

* fields / can be templated
  * -- depend on -- contact point integration

![](/grafana/media/docs/alerting/how-notification-templates-works.png)

## More information

* [Notification Templating tutorial](https://grafana.com/tutorials/alerting-get-started-pt4/).
