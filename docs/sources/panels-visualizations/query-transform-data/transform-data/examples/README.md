* `docker compose up -d`
* http://localhost:3000/
  * admin/admin
  * Data sources > Add data source > Prometheus
    * Connection: http://host.docker.internal:9090

* Dashboard > New Dashboard > Original > Grafana
* Dashboard > New Dashboard > Original > Grafana
  * dashboard | make adjustments

# manipulate data / returned by a query BEFORE visualizing
* SECOND dashboard
  * Transformations > Reduce > 
    * Mode: Series to rows
    * Calculations: Last*
  * choose table

# Order of transformations
## follow the order / they are listed
* SECOND dashboard
  * Transformations > Reduce >
    * Mode: Series to rows
    * Calculations: Last*
  * Add another transformation >
    * Mode: Series to rows
    * Calculations: Max
  * ONLY display MAX

# Dashboard variables in transformations
## interpolated BEFORE the transformation
* TODO:

# Transformation functions
## Add field from calculation
* Dashboard > New Dashboard > Datasource = TestData
  * Query A
    * Scenario == CSV Content
      ```
      server,cpu_usage,memory_usage,requests,errors
      web-01,80,60,1000,10
      web-02,75,70,800,5
      db-01,90,85,500,2
      ```
* Transformation > Add field from calculation
  * Mode
    * == Unary operation
      * Operation == `exp(cpu_usage)`
    * == Binary operation
      * Operation = 
        * case1
          * `cpu_usage+memory_usage`
          * alias = total_usage
        * case2
          * `errors/requests`
          * error rate
    * == Reduce row
      * Operation == cpu_usage, memory_usage
      * Calculation = Last
    * Cumulative functions
      * Field = memory_usage
      * Calculation 
        * Total
        * Mean

## Filter data by values
* Dashboard > New Dashboard > Datasource = TestData
  * Query A
    * Scenario == CSV Content
    ```
    server,status,cpu_usage,region,environment
    web-01,active,85,us-east,prod
    web-02,inactive,45,us-east,staging
    db-01,active,92,us-west,prod
    db-02,active,67,us-west,staging
    cache-01,inactive,23,eu-central,dev
    ```
* Transformation > Filter data by values
  * Filer type = Include
  * Conditions = Match any
  * Field
    * server = web-01
  * try
    * add more conditions
    * switch 
      * Filter type
      * Conditions

## Reduce
* Dashboard > New Dashboard > Datasource = TestData
  * Query A
    * Scenario == CSV Content
    ```
    web-01_cpu,web-02_cpu,db-01_cpu
    80,75,90
    85,70,95
    78,72,88
    82,74,92
    ```
### return 1! value
* Transformation > Reduce > Mode = serires to rows > Calculations = Max
### modes
#### Reduce fields
* Transformation > Reduce > Mode = Reduce fields > Calculations = Max
  * ONLY 1!  column
#### Series to rows
* Transformation > Reduce > Mode = serires to rows > Calculations = Max
  * filter & convert to rows

## Group by
* Dashboard > New Dashboard > Datasource = TestData
  * Query A
    * Scenario == CSV Content
      ```
      Time,Server,Region,CPU,Memory
      2023-01-01,web1,us-east,80,60
      2023-01-01,web2,us-east,75,65
      2023-01-01,web3,us-west,90,70
      2023-01-01,db1,us-east,85,80
      2023-01-01,db2,us-west,70,75
      ```
  * Transformation > Group by > 
    * Region
      * Group by
      * Select Stats = Count
    * CPU
      * Calculate
      * Max

## Join by field
* Dashboard > New Dashboard > Datasource = TestData
  * Query A
    * Scenario == CSV Content
      ```
      server_id,hostname,region,cpu_cores
      1,web-01,us-east,4
      2,web-02,us-east,8
      3,db-01,us-west,16
      4,db-02,us-west,32
       ```
  * Query B
    * Scenario == CSV Content

    ```
    server_id,cpu_usage,memory_usage,disk_usage
    1,75,60,45
    2,80,70,50
    3,90,85,60
    4,65,75,40
    ```
### Inner join
* Transformation > Join by field
  * Mode = Inner
  * Field = server_id
### Outer join (tabular)
* Transformation > Join by field
  * Mode = Inner
  * cases
    * Field = server_id
      * matching + 2@ Query
    * Field = hostname
      * ONLY hits / has hostname
        * Reason: 🧠STILL it's a join🧠
### Outer join (time series)
* TODO:
