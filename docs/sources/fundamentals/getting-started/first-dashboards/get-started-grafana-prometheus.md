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

## Download Prometheus and Node exporter

- [Prometheus](https://prometheus.io/download/#prometheus)
- [Node exporter](https://prometheus.io/download/#node_exporter)

## Install Prometheus Node exporter

* [Prometheus Node exporter's instalation & running](https://prometheus.io/docs/guides/node-exporter/#installing-and-running-the-node-exporter)
* http://localhost:9100/metrics
  * exporting metrics

## Install and configure Prometheus

* `docker compose up -d`

## Configure Prometheus for Grafana
### | Grafana Cloud](/) or run 
* | prometheus.yml
  ```yaml
  remote_write:
    - url: <https://your-remote-write-endpoint>
      basic_auth:
        username: <your user name>
        password: <Your Grafana.com API Key>
  ```

### Grafana locally

* follow [this](/grafana/docs/sources/datasources/prometheus/configure)
