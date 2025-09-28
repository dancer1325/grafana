# Query inspector UI
* [Grafana Playground](https://play.grafana.org/goto/bezfdlrve8q2oa?orgId=1)
## Query tab
* [Grafana Playground](https://play.grafana.org/goto/bezfdlrve8q2oa?orgId=1)
  * `process_cpu_seconds_total`
  * request's url "api/ds/query?ds_type=prometheus&requestId=explore_emr"
    * ds  
      * == data source
    * query
      * == query operation
    * ds_type=prometheus
      * == data source type
    * requestId=explore_emr
      * explore
        * == comes from Explore section
## Data tab
### download | .txt
* [Grafana Playground](https://play.grafana.org/goto/eezffucaqyku8c?orgId=1)
  * `cluster` & choose some value
## Error tab
### ONLY if query returns an error
* [Grafana Playground](https://play.grafana.org/goto/bezfdlrve8q2oa?orgId=1)
  * `process_cpu_seconds_total sum`
