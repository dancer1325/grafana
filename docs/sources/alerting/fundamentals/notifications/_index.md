---
aliases:
  - ./notification-policies/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notification-policies/
canonical: https://grafana.com/docs/grafana/latest/alerting/fundamentals/notifications/
description: Learn about how notifications work
keywords:
  - grafana
  - alerting
  - notification policies
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Notifications
weight: 110
refs:
  alert-rule-evaluation:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rule-evaluation/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rule-evaluation/
  group-alert-notifications:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/group-alert-notifications/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/group-alert-notifications/
  templates:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/templates/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/templates/
  configure-alertmanager:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/set-up/configure-alertmanager/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/set-up/configure-alertmanager/
  notification-policies:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/notification-policies/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/notification-policies/
  notification-timings:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/group-alert-notifications/#timing-options
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/group-alert-notifications/#timing-options
  silences:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/create-silence/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/create-silence/
  mute-timings:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/mute-timings/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/mute-timings/
  contact-points:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/contact-points/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/contact-points/
---

# Notifications

* 👀ways to send your alerts👀
  * [contact points](ref:contact-points) 
  * [Notification Policy Tree](#notification-policies)
    * allows
      * flexibly route alerts -- to -- contact points

![](/grafana/media/docs/alerting/alerting-configure-notifications-v2.png)

## How does it work?

- Grafana alerting 
  - periodically [evaluates your alert rules](ref:alert-rule-evaluation)
  - if alert instances are **firing** OR **resolved** -> triggers notifications
  - if you want to reduce the number of notifications -> **group related alerts** -- , via label grouping & notification timings, into -- 1! notification 

## Fundamentals

### Contact points

* == how to receive your alert notifications
* == destinations (email, Slack, IRM, webhooks, ...) + notification messages
  * notification messages
    * by default, contains: number of alerts + alert names + labels + annotations + other alert information
    * ways to customize
      * manually
      * -- via -- notification templates

### Notification policies

* allows
  * flexibly route alerts -- to -- contact points 

* uses
  * define nested policies / can inherit OR overwrite parent notification settings
  * route alerts -- , by matching alert labels, to the -- appropriate notification policy

  ![](/grafana/media/docs/alerting/notification-routing.png)

* task handled / EACH notification policy
  - decide the contact point / receives the alert notification
  - when to send notifications -- based on -- notification timing options
  - grouping MULTIPLE alerts -- into a -- 1! notification

  ![](/grafana/media/docs/alerting/alerting-notification-policy-diagram-v5.png)

### Group alert notifications

* MULTIPLE alert instances are combined -- into -- 1! notification
  * -- based on --
    * **Labels**
    * **Timing options**
      * BEFORE sending the notification, wait for a specified period
* allows
  * avoid bombarding MULTIPLE related alert instances
    * _Examples:_ if cluster is down -> pods are down -> ONLY fire 1 notification about cluster is down

* [MORE](ref:group-alert-notifications)

### Templates, silences and mute timings

* Grafana Alerting's ADDITIONAL configurations 
  * shared [templates](ref:templates)
  * [silences](ref:silences) & [mute timings](ref:mute-timings)
    * WITHOUT interrupting alert evaluation,
      * pause or suppress notifications

## Architecture

* Grafana Alerting
  * 's model
    * built | Prometheus model
    * == 
      * **alert generator**
        * responsible for
          * evaluates alert rules
          * sends firing and resolved alerts -- to the -- alert receiver
      * **alert receiver**
        * built-in Grafana Alertmanager
        * responsible for
          * receives the alerts
          * send alert's notifications
    * Reason:🧠scalability & performance🧠

![](/grafana/media/docs/alerting/alerting-alertmanager-architecture.png)
