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
* **Alerting** -> **Alert rules** > **More** -> **New data source-managed recording rule**
  * Enter recording rule
    * name: datasourcemanagedrecordingrule
  * Define recording rule
    * data source
      * Problems:
        * Problem1: NOTHING appear
          * Note1: NOT related to exist ALREADY a record rule | data source
          * Note2: valid | grafana cloud / enabled -- via -- Administration -> Plugins and Data -> Recorded queries
          * Solution: TODO:
    * query
      * == instant queries
  * Add namespace and group
    * namespace
      * datasourcemanagedrecordingrule
    * group
      * datasourcemanagedrecordingrule
  * Add labels
    * OPTIONAL
    * == NEW metric's labels
