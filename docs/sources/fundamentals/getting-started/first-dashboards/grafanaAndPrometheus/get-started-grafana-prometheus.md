---
aliases:
  - ../../../getting-started/getting-started-prometheus/ #/docs/grafana/latest/getting-started/getting-started-prometheus
  - ../../../getting-started/get-started-grafana-prometheus/
description: Learn how to build your first Prometheus dashboard in Grafana.
labels:
  products:
    - enterprise
    - oss
title: Get started with Grafana and Prometheus
weight: 300
---

# Get started with Grafana and Prometheus

* goal
  * create dashboards | Grafana /
    * display server's system metrics / monitored -- by -- Prometheus

* Prometheus
  * monitoring system
  * open source
* Grafana
  * provides
    * out-of-the-box support -- for -- Prometheus

## requirements
- [Prometheus](https://prometheus.io/download/#prometheus)
- [Node exporter](https://prometheus.io/download/#node_exporter)
  - ['s instalation & running](https://prometheus.io/docs/guides/node-exporter/#installing-and-running-the-node-exporter)
  * http://localhost:9100/metrics
    * exporting metrics

## steps

* `docker compose up -d`

### Configure Prometheus for Grafana
#### Cloud
* | Grafana Cloud Portal
  * Details > Prometheus > Send metrics > Sending metrics with Prometheus > Generate a token

#### Local

* follow [this](/grafana/docs/sources/datasources/prometheus/configure)

### check metrics are workin
#### | Grafana Cloud
* Launch Grafana > Drilldonw > Metrics
#### | Grana local
* follow [this](/grafana/docs/sources/datasources/prometheus/configure)
