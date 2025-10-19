* `docker compose up -d`
* http://localhost:3000/
  * admin/admin

# requirements
## TSDB
* Connections > Data source > Add new data source 
  * Prometheus
    * Prometheus server URL: http://prometheus:9090

## Prometheus-based data source's CL's flag `web.enable-remote-write-receiver`
* see [docker-compose.yml](docker-compose.yml)

# create a recording rule
* Alerting > Alert rules > New recording rule > New recording rule
  * Enter recording rule and metric name
    * name: recordingRuleGrafanaManagedFirst
    * metric: recordingrulegrafanamanagedfirst
    * target data source: Prometheus
  * Define recording rule
    * query A: `histogram_quantile(0.95, sum(rate(prometheus_http_request_duration_seconds_bucket[5m])) by (le, handler)) /
      avg(rate(prometheus_http_requests_total[5m])) by (handler)`
  * Add folder and labels
    * recordingRuleGrafanaManagedFirst
  * Set evaluation behavior
    * name: recordingRuleGrafanaManagedFirst
    * interval: 10s

# Define recording rule's restrictions
## NEW metric name MUST follow Prometheus metric names
* TODO:

## Options dropdown time range / fixed relative time ranges & NOT support absolute time ranges
* check PREVIOUS steps | create 

# AFTER creating it, available the NEW metric
* Explore > 
  * Data source: Prometheus
  * Query: `recordingrulegrafanamanagedfirst`
