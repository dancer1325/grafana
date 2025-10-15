* `docker run -d -p 3000:3000 grafana/grafana`
* http://localhost:3000/
  * admin / admin
* Dashboard > New Dashboard > Settings > Variables > Add variable
  * Variable Type == whatever 
  * value = alfred


# title & description
## ALLOWED to use / variables defined
* Dashboard > edit > Panel options >
  * Title = ${query0}
  * Description = ${query0}
## NOT ALLOWED to use / global variables
* Dashboard > edit > Panel options >
  * Title = $__dashboard
  * Description = $__dashboard


#  configure repeating panels
* Dashboards > 
  * Settings > Variables > Add variable > 
    * Variable type = custom
    * name = servers
    * Custom options= server1,server2,server3
    * Multi-value: ✅ Enabled
    * Include All option: ✅ Enabled
  * Add visualization > Time series
    * Data source = TestData DB
    * Scenario = Random Walk
    * Alias = cpu usage -${servers}
  * Panel options > Repeat options
    * Repeat by variable = servers
    * Repeat direction = horizontal
    * Max per row: 2
  * Save Dashboard > back to dashboard
