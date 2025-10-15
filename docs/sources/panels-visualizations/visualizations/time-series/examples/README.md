# default way / show the variations of a set of data values | time
* `docker run -d -p 3000:3000 grafana/grafana`
* http://localhost:3000/
* admin / admin
* **Dashboards** > **New** > **Add visualization** > preselect the time series

# if there are >1 numerical data -> EACH one is plotted | NEW line, point, or bar labeled
* [link](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=2025-10-10T06:26:43.638Z&to=2025-10-10T07:26:43.638Z&timezone=browser&editPanel=1&viewPanel=panel-1)
* 👀uncomment 1 query👀

# uses
## DIFFICULT to track | table
* [here](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser&tab=queries&editPanel=1)
  * click table view OR switch visualization to table

# Supported data formats
## if the time field is NOT AUTOMATICALLY detected -> convert the data -- , via [data transformation](ref:panel-data-section), to a -- time format
* Connections > Data sources > testdata > Save & test
* Dashboard > Visualization > Add visualization >
  * Data source = Testdata
  * Scenario = CSV Content
  ```
  timestamp_str,cpu_usage,memory_usage
  "2024-01-15 10:00:00",45.2,67.8
  "2024-01-15 10:05:00",48.1,69.2
  "2024-01-15 10:10:00",52.3,71.5
  "2024-01-15 10:15:00",49.7,68.9
  ```
  * Transformation > Convert field type
    * Field = timestamp_str
      * as Time
      * Input format == YYYY-MM-DD HH:mm:ss
## formatted -- as a -- table /
* [here](https://play.grafana.org/goto/af0m4sjm36vi8c?orgId=1)
  * see table-related
  * [visualization-related](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser&tab=queries&editPanel=1)

# Alert rules
## link alert rules
* [Grafana playground](https://alfredotic0809.grafana.net/d/b572f479-0c5d-4e28-a716-8ee0e24a1cbd/billing-usage?orgId=1&from=now%2FM&to=now&timezone=utc&var-org_slug=alfredotic0809&var-org_id=1537652&var-metrics_id=$__all&var-logs_id=$__all&var-traces_id=$__all&var-grafana_id=$__all&var-profiles_id=$__all&var-eval_time=1760299545&var-is_customer_of_grafana=1&var-is_customer_of_partner=0&editPanel=29&tab=alert)

# Special overrides
## Transform override property
* [Grafana playground](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser&editPanel=1)
  * Add field override > Field with name == backend01 > **Graph styles > Transform** [override property](#field-overrides)
    * switch BETWEEN values
## Fill below to override property
* [Grafana playground](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser&editPanel=220)
  * Add field override > whatever > **Graph styles > Fill below to** [override property](#field-overrides)
    * Field with name: higher serie
    * Fill below to: intermediate one
