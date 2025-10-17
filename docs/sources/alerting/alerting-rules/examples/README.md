* `docker run -d -p 3000:3000 grafana/grafana`
* localhost:3000
  * admin/admin

# requirements: compatible Data source
* Alerting > Alert rules > New Alert rule
  * | 2. Define query and alert condition, ⚠️IMPOSSIBLE ⚠️
    * Solution: 
      * `docker run -p 9090:9090 prom/prometheus`
      * Connections > Data source > Add new data source > Prometheus
        * Prometheus Server URL = host.docker.internal:9100

# Alert rule == >=1 queries + condition + evaluation period + ADDITIONAL options
* Alerting > Alert rules > New Alert rule
  * \>=1 queries + condition
    * == section 2
  * evaluation period
    * == section 4
  * ADDITIONAL options
    * == REST of sections

# supported types alert rules
* `docker kill grafana`
* `docker compose up -d`
## **Grafana-managed alert rules**
* Alerting > Alert rules > New alert rule >
  * Name: grafana-managed alert rule
  * Define query
    * up
    * ABOVE 1
  * Add folder and labels: 
    * Grafana Managed Rule
    * key1/value1
    * key2/value2
  * Notifications: grafana-default-email
## **Data source-managed alert rules**
### == alert rules / stored | data source itself
* Alerting > Alert rules
  * ALREADY appear | specific section

