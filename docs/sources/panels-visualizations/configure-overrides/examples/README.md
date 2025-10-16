* `docker run -d -p 3000:3000 grafana/grafana`
* http://localhost:3000/
  * admin / admin


* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Time series
  * Queries
    * QueryA
      * Data source: TestData
      * Scenario: Random Walk
      * Alias: cpu_usage_server1
    * Query B:
      * Data source: TestData DB
      * Scenario: CSV Metric Values
      * String input: 1,50.5,2,75.2,3,90.8
      * Alias: memory_usage_server2
    * Query C:
      * Data source: TestData DB
      * Scenario: CSV Metric Values
      * String input: 1,25,2,30,3,35
      * Alias: disk_usage_server3


# Fields with name
* Add field override=Fields with name > cpu_usage_server1
  * Add override property
    * Standard options > Color 
    * Axis → Placement: Left

# Field with name matching regex
* Add field override=Fields with name matching regex > `.*_usage_.*`
  * Add override property
    * Standard options → Unit: Percent (0-100)

# Fields with type
* Add field override=Fields with type > number
  * Add override property
    * Standard options → decimals:2

# Fields returned by query
* Add field override=Fields returned by query > B
  * Add override property
    * Standard options → Color: Choose another

# Fields with values
* Add field override=Fields with value > Last > 80
  * Add override property
    * Thresholds > 
      * base=0
      * red=80
