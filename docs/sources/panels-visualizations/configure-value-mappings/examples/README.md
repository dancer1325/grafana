* `docker run -d -p 3000:3000 grafana/grafana`
* http://localhost:3000/
  * admin / admin

# Value mappings
## bypass **Standard options**'s unit formatting
### number of decimal places
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Stat
  * Query1 > Datasource=TestData > 
    * Scenario = CSV Metric Values
    * String input = 1,75.123456
  * Standard options >
    * Unit: Percent (0-100)
    * Decimals: 0
  * Without adding value mapping
    * hover | data point = 75%
  * With value mapping
    * Value mapping > Add value mappings
      * Value: 75.123456
      * Display text = Excellent Performance
### color
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Gauge
  * Query1 > Datasource=TestData >
    * Scenario = CSV Metric Values
    * String input = 1,50
  * Standard options >
    * Color schema: Green-Yellow-Red
  * Thresholds >
    * 70
  * With value mapping
    * Value mapping > Add value mappings
      * Value: 50
      * set color = yellow


## Types of value mappings
### value
* **Dashboards** > **New** > **Add visualization** >
  * Query1 > Datasource=TestData >
    * Scenario = CSV Metric Values
    * String input = 1,50,30,60,20,50,150,200
  * Value mapping > Add value mappings
    * Value: 50
    * Display text = Alfred

### Range
* **Dashboards** > **New** > **Add visualization** >
  * Query1 > Datasource=TestData >
    * Scenario = CSV Metric Values
    * String input = 1,50,30,60,20,50,150,200, 300
  * Value mapping > Add value mappings
    * Range: [20, 60]
    * Display text = Alfred

### Regex
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Table
  * Query1 > Datasource=TestData >
    * Scenario = CSV Content
    * String input

      ```
      Time,Server
      1,www.example.com
      2,api.github.com
      3,docs.grafana.com
      4,www.stackoverflow.com
      5,mail.google.com
      ```
  * Value mapping > Add value mappings
    * Case1
      * Regex: ^([^.]+)\..*
      * Display text = ${__value.capture(1)}
      * Color: blue
    * Case2
      * Regex: .*\.([^.]+)\.com$
      * Display text: ${__value.capture(1)} Service
      * Color: green
    * Problems: NOT displayed the colors
      * Solution: TODO:

# Special
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Table
  * Query1 > Datasource=TestData >
    * Scenario = CSV Content
    * String input
    
    ```
    Time,Status
    1,Active
    2,
    3,Inactive
    4,
    5,Active
    ```
  * Value mapping > Add value mappings
    * Case1
      * Special: null
      * Display text: N/A
    * Case2
      * Special: true
      * Display text: ✅
