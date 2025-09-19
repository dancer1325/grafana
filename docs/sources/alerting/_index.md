---
aliases:
  - about-alerting/ # /docs/grafana/<GRAFANA_VERSION>/about-alerting
  - ./unified-alerting/alerting/ # /docs/grafana/<GRAFANA_VERSION>/unified-alerting/alerting/
  - ./alerting/unified-alerting/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/
canonical: https://grafana.com/docs/grafana/latest/alerting/
description: Learn about the key benefits and features of Grafana Alerting
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Alerting
title: Grafana Alerting
weight: 114
hero:
  title: Grafana Alerting
  level: 1
  image: /media/docs/grafana-cloud/alerting-and-irm/grafana-icon-alerting.svg
  width: 100
  height: 100
  description: Grafana Alerting allows you to learn about problems in your systems moments after they occur.
cards:
  title_class: pt-0 lh-1
  items:
    - title: Introduction
      href: ./fundamentals/
      description: Learn more about the fundamentals and available features that help you create, manage, and respond to alerts; and improve your team’s ability to resolve issues quickly.
      height: 24
    - title: Configure alert rules
      href: ./alerting-rules/
      description: Create, manage, view, and adjust alert rules to alert on your metrics data or log entries from multiple data sources — no matter where your data is stored.
      height: 24
    - title: Configure notifications
      href: ./configure-notifications/
      description: Choose how, when, and where to send your alert notifications.
      height: 24
    - title: Monitor status
      href: ./manage-notifications/
      description: Monitor, respond to, and triage issues within your services.
      height: 24
    - title: Additional configuration
      href: ./set-up/
      description: Use advanced configuration options to further tailor your alerting setup. These options can enhance security, scalability, and automation in complex environments.
      height: 24
---

{{< docs/hero-simple key="hero" >}}

---

## Overview

* goal
  * monitor your 
    * incoming metrics data OR
    * log entries
  * set up your Grafana Alerting system
    * -- based on -- specific events or circumstances

* pros  
  * eliminate manual monitoring
  * notice system outages OR changes
  * create queries & expressions -- from -- 👀MULTIPLE data sources👀
    * _Examples:_ metrics + logs + profiling issues

## Explore

{{< card-grid key="cards" type="simple" >}}
