* `docker compose up -d`
* Connections > Data sources > Add new data source >
  * Prometheus > 
    * ways
      * -- via -- real Prometheus
        * Prometheus Server URL: http://prometheus:9090
      * -- via -- Mimir
        * Name: Mimir
        * Prometheus Server URL: http://mimir:9009
  * Alertmanager > 
    * Implementation: Prometheus
    * HTTP=http: http://alertmanager:9093
  * Loki >
    * URL: http://loki:3100

# about Grafana Mimir's alert rules & Grafana Loki's alert rules,
## create
* Grafana UI > Alerting > Alert rules >New alert rule > 
  * name: lokiCreatedInGrafana
  * Define query and alert condition
    * data source: loki
    * expression: count_over_time({filename="/var/log/docker.log"}[5m]) > 0
    * condition: Last above 600
  * Add folder and labels
    * Folder > New folder: Loki
    * Labels > key1/value1
  * Set evaluation behavior > New > Loki
  * Problems:
    * Problem1: appear as Grafana-managed rule
      * Solution: TODO: ❓
## edit
* Grafana UI > Alerting > Alert rules > Data source managed rules
  * Problems:
    * Problem1: ONLY view or duplicate
      * Solution: TODO: ❓

# about Prometheus data sources,
## if "Manage alerts via Alerting UI" is enabled -> view rules
* Connections > Data sources > Prometheus >
  * switch on & off "Manage alerts via Alerting UI"
## ❌NOT possible to create or edit them❌
* Grafana > Alerting > Alert rules > Data source managed rules > NOT possible to create OR edit them



# Grafana-managed rules vs data source-managed alert rules
## supported data sources
* == BEFORE

## Mix and match data sources
* Grafana > Alerting > Alert rules > New alert rule > 
  * Name: Mix data sources
  * Define query and alert condition > 👀Advanced options (enable add MULTIPLE queries)👀
    * queries
      * query A: `up{instance="loki:3100"}`
      * query B: `up{instance="localhost:9090"}`
    * expressions
      * Input: A is below to 1 
    * condition: Last above 600
  * Add folder and labels
    * Folder > New folder: Mix data sources
    * Labels > key1/value1
  * Set evaluation behavior > New > Mix data sources

## expressions
