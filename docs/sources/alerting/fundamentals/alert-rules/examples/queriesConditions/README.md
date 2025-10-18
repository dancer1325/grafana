* `docker compose up -d`
* http://localhost:3000/
* Connections > Data sources > Add data source
  * Prometheus >
    * Prometheus Server URL: http://prometheus:9090
  * Alertmanager >
    * Implementation: Prometheus
    * HTTP=http: http://alertmanager:9093
  * Loki >
    * URL: http://loki:3100

# Alerting queries editor
## customized user interface / data source
* Alerting > Alert rules > New alert rule
  * Define query and alert condition
    * switch between Loki & Prometheus

# ALLOWED data types
## Time series data
### EACH series must be reduced -- to a -- 1! numeric value
* Grafana > Alerting > Alert rules > New alert rule >
  * Name: ALLOWED data types - time series data 
  * Define query and alert condition
    * query: `prometheus_http_requests_total`
    * alert condition
      * when query Is above:0
#### OTHERWISE -> error
* Grafana > Alerting > Alert rules > New alert rule >
  * Name: ALLOWED data types - time series data
  * Define query and alert condition
    * query: `prometheus_http_requests_total[5m]`
    * alert condition
      * when query Is above:0 -- ❌NOT valid ❌
### EACH time series is evaluated -- as a -- separate alert instance
* Grafana > Alerting > Alert rules > New alert rule >
  * Name: ALLOWED data types - time series data
  * Define query and alert condition
    * query: `prometheus_http_requests_total`
    * alert condition
      * when query Is above:0
      * 👀you see DIFFERENT alert instances👀
## Tabular data
### 1! numeric column / EACH row
* TODO:
### EACH time series or table row is evaluated -- as a -- separate alert instance
* TODO:

# Alert condition
## | use **Default options**,
* Grafana > Alerting > Alert rules > New alert rule >
  * Name: Alert condition - default options
  * Define query and alert condition
    * query: `prometheus_http_requests_total`
    * alert condition
## | use **Advanced options**, you can choose
* Grafana > Alerting > Alert rules > New alert rule >
  * Name: Alert condition - advanced options
  * Define query and alert condition > 👀Advanced options (enable add MULTIPLE queries)👀
    * query: `prometheus_http_requests_total`
    * expressions
      * expression1: Threshold
        * Input: A
        * Is above:1
        * click as alert condition

# Expressions
## requirements: Grafana-managed alerts + enable the **Advanced options**
* Alerting > Alert rules > New alert rule > Define query and alert condition
  * switch on & off Advanced options
## Reduce
* Grafana > Alerting > Alert rules > New alert rule >
  * Name: Reduce
  * Define query and alert condition > 👀Advanced options (enable add MULTIPLE queries)👀
    * query: `prometheus_http_requests_total[5m]`
    * expressions
      * expression1: Reduce
        * Input: A
        * Function: Mean
      * expression2: Threshold
        * Input: B
        * Is above:1
        * click as alert condition
  * Add folder and labels
    * Folder > New folder: Query conditions
    * Labels > function/reduce
  * Set evaluation behavior > New > Query conditions
## Math
### uses |
#### query / if series have SAME labels -> joined
* TODO:
#### expression's alert condition
* Grafana > Alerting > Alert rules > New alert rule >
  * Name: Math
  * Define query and alert condition > 👀Advanced options (enable add MULTIPLE queries)👀
    * query: `prometheus_build_info`
    * expressions
      * expression1: Math
        * Expression: `$A + 2`
        * AUTOMATICALLY, alert condition
## Resample
* TODO:
## Threshold
* TODO:
## Recovery threshold
* TODO:
## Classic condition (legacy)
* TODO:
