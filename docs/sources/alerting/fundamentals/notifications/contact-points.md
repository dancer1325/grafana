---
aliases:
  - ../../fundamentals/contact-points/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/contact-points/
  - ../../fundamentals/contact-points/contact-point-types/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/contact-points/contact-point-types/
  - ../../contact-points/ # /docs/grafana/<GRAFANA_VERSION>/alerting/contact-points/
  - ../../unified-alerting/contact-points/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/contact-points/
canonical: https://grafana.com/docs/grafana/latest/alerting/fundamentals/notifications/contact-points/
description: Learn about contact points and the supported contact point integrations
keywords:
  - grafana
  - alerting
  - guide
  - contact point
  - notification channel
  - create
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Contact points
weight: 112
refs:
  configure-contact-points:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/manage-contact-points
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/manage-contact-points
---

# Contact points

* == 👀configuration👀
  * -- for -- sending alert notifications
  * ways to assign
    * | alert rule, OR
    * | notification policy options
  * ⚠️requirements⚠️
    * \>=1 contact point integrations
      * ❌== if you configure a contact point / NO integrations -> notifications are NOT sent❌
  * [how to configure](ref:configure-contact-points)

* supported contact point integrations
  - Alertmanager
  - Amazon SNS
  - Cisco Webex Teams
  - DingDing
  - Discord
  - Email
  - Google Chat
  - Grafana IRM
  - Jira
  - Kafka REST Proxy
  - Line
  - Microsoft Teams
  - MQTT
  - Opsgenie
  - PagerDuty
  - Pushover
  - Sensu Go
  - Slack
  - Telegram
  - Threema Gateway
  - VictorOps
  - Webhook
  - WeCom

* contact point integration's configuration
  * message / send
    * ALLOWED ones
      * predefined message,
      * custom message,
      * template message
