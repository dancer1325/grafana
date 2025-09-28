# Pre-requirements
* `docker run -d -p 3000:3000 grafana/grafana`

# Grafana Explore
## mixing data sources
* [Grafana playground > explore > Mixed](https://play.grafana.org/goto/bezf5eoow4e0wd?orgId=1)
  * Prometheus
    * `sum(prometheus_remote_storage_highest_timestamp_in_seconds)`
  * Loki
    * `container=alloy-operator`
## aggregating data
* [Grafana playground > explore > Prometheus data source](https://play.grafana.org/goto/dezf576pu2z28a?orgId=1)
  * `sum(prometheus_remote_storage_highest_timestamp_in_seconds)`
