* `docker run -d -p 3000:3000 grafana/grafana`
* localhost:3000
  * admin/admin
  * Connections > Data sources > Add data source > Testdata

# save the results -- as -- NEW time series metrics
* Alerting > Alert rules > New recording rule > choose whatever (grafana OR data source-managed)
  * Enter recording rule and metric name
    * name: recordingRuleFirst
    * metric: recordingrulefirst
    * target data source: TODO:
  * Define recording rule
    * TODO:

# NEW time series metrics uses
## OTHER alert rules
* TODO:
## OTHER dashboard queries
* TODO:
