* `docker run -d -p 3000:3000 grafana/grafana`

* http://localhost:3000/
* admin / admin
* **Dashboards** > **New** > **Add visualization** >
  * Visualization: Panel
  * Data source: TestData DB

# Calculation type
## 1st % - 99th %
* Scenario: CSV Metric Values
* String input: 1,50,2,75,3,100,4,125,5,150,6,200,7,300,8,500,9,1000,10,2000
* Value options > Show=Calculate
  * Calculation = choose DIFFERENT `%`

## All nulls
* Scenario: CSV Content
* String input:
  * case 1
    ```
    Time,Server1,Server2
    1,,aaa
    2,,
    3,,
    ```
    * Value options > Show=Calculate
      * Calculation = All Nulls
      * Fields: All fields
        * -> ⚠️server2 = true⚠️
          * Reason:🧠string is interpreted -- as -- not number == null🧠
  * case 2
    ```
    Time,Server1,Server2
    1,,22
    2,,
    3,,
    ```
    * Value options > Show=Calculate
      * Calculation = All Nulls
      * Fields: All fields
        * -> server2 = false
          * Reason:🧠it contains a row with a number🧠

## All unique values
* Scenario: CSV Content
* String input:
  ```
  Time,Status
  1,Running
  2,Stopped
  3,Error
  4,Running
  ```

* Value options > Show=Calculate
  * Calculation = All unique values
  * Fields: Status

## All zeros
* Scenario: CSV Metric values
* String input: 1,0,2,0,3,0,4,0
* Value options > Show=Calculate
  * Calculation = All zeros
  * Fields: A-series

## Change count
* Scenario: CSV Metric values
* String input: 1,0,2,0,3,0,4,0
* Value options > Show=Calculate
  * Calculation = Change count
  * Fields: A-series

## Count
* Scenario: CSV Metric values
* String input: 1,0,2,0,3,0,4,0,null,0,null
* Value options > Show=Calculate
  * Calculation = count
  * Fields: A-series

## Delta
* Scenario: CSV Metric values
* Value options > Show=Calculate
  * Calculation = Delta
  * Fields: A-series
* String input: 
  * case1: 100, 110, 90, 120
    * -> ONLY FIRST 10
  * case2: 100, 90, 120
    * -> consider reset -> 0
  * cas3: 100, 110, 120, 180, 190
    * -> 90


## Difference
* Scenario: CSV Metric values
* String input: 100, 50, 190
* Value options > Show=Calculate
  * Calculation = DIFFERENCE
  * Fields: A-series

## TODO:
