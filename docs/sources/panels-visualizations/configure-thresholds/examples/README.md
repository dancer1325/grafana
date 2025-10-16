* `docker run -d -p 3000:3000 grafana/grafana`
* http://localhost:3000/
  * admin / admin

# use cases
## | time series visualization, color grid lines & regions
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Time series
  * Query1 > Datasource=TestData >
    * Scenario = Random Walk
    * Min: 0
    * Max: 100
  * Thresholds >
    * values
      * threshold: 0 (green)
      * threshold: 30 (yellow)
      * threshold: 70 (orange)
      * threshold: 90 (red)
    * show thresholds: As filled regions and lines
  * Refresh data if they are NOT displayed

## | stat visualization, color the background OR value text
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Stat
  * Query1 > Datasource=TestData >
    * Scenario = CSV Metric Values
    * String input: 1,85
  * Thresholds >
    * values
      * threshold: 0 (green)
      * threshold: 50 (yellow)
      * threshold: 80 (red)
  * Stat styles
    * Color mode =
      * value -> red text
      * background -> red background
  * if you adjust the string input -> see the difference
    * String input: 1,25
    * String input: 1,55

## | state timeline, define regions & region colors
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Stat
  * Query1 > Datasource=TestData >
    * Scenario = CSV Metric Values
    * String input: 1,0,2,1,3,2,4,1,5,3,6,2,7,0,8,3
  * Thresholds >
    * threshold: 0 (green)
    * threshold: 1 (yellow)
    * threshold: 2 (red)

## | gauge, color the gauge & threshold markers
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Gauge
  * Query1 > Datasource=TestData >
    * Scenario = CSV Metric Values
    * String input: 1,75
  * Thresholds >
    * threshold: 0 (green)
    * threshold: 50 (yellow)
    * threshold: 60 (red)

## | table, color cell text or background
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Table
  * Query1 > Datasource=TestData >
    * Scenario = CSV Content

    ```
    Time,Server,CPU,Memory,Status
    1,Server1,25,45,1
    2,Server2,75,60,2
    3,Server3,95,85,3
    4,Server4,40,30,1
    ```

  * Add field override > Fields with name: CPU > Add override property = Thresholds
    * threshold: 0 (green)
    * threshold: 50 (yellow)
    * threshold: 60 (red)
  * Cell options > Cell type = whatever (_Example:_ colored background)
    * -> override ALREADY displayed / override

# Thresholds options
## Thresholds mode
### Percentage
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Gauge
  * Query1 > Datasource=TestData >
    * Scenario: CSV Metric Values
    * String input: 1,150
  * Standard options >
    * Min: 0
    * Max: 200
    * Unit: Short
  * Thresholds
    * values
      * value1: 0%
      * value2: 50%
      * value3: 80%
    * mode: percentage



## Show thresholds
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Time series
  * Query1 > Datasource=TestData >
    * Scenario = CSV Metric Values
    * String input: 1,20,90,30,5,0
  * Thresholds >
    * values
      * threshold: 0 (green)
      * threshold: 30 (yellow)
      * threshold: 70 (orange)
      * threshold: 90 (red)
    * show thresholds:
      * SWITCH BETWEEN ALL OF THEM
