https://grafana.com/docs/grafana-cloud/machine-learning/dynamic-alerting/outlier-detection/

* goal
  * create an Outlier Detector
  * set up outlier-based alerts 

* Grafana AI’s outlier detection
  * allows
    * 👀identify some group's members behavior != rest members behavior👀 
      * == forecast anomalies
  * requirements
    * Grafana cloud
    * Editor permissions
    * \>= 3 series
  * _Example of uses:_
    * how the load is distributed ACROSS Grafana Mimir ingester
  * 's algorithm
    * 's inputs
      * sensitivity -- to -- your liking
        * higher sensitivity -> MORE outliers & alerts fired 
    * built-in algorithms
      * DBSCAN (Density-based spatial clustering of applications with noise)
        * == cluster data points -- based on -- their density 
          * updated CONTINUOUSLY
        * use cases
          * series move in sync | time
          * strong trends | your data 
      * MAD (Median Absolute Deviation)
        * 's inputs
          * sensitivity threshold
        * compares
          * data points | EACH timestamp vs rolling 24-hour median 
        * use cases
          * ALL group's members move | stable band of normal behavior / NO affected by out-of-sync events
  * 👀| save it -> NEW metric is exposed | Prometheus's `grafanacloud-ml-metrics`👀
    * `<outlier_detector_metric_name>:outliers`
      * 's return
        * binary
          * 0 == NO outlier
          * 1 == outlier

* Outlier Detector query
  * == series / are compared + baseline group

## how to create
### outlier detection
* AI & machine learning > Outlier detection > add query
### outlier-based alert
* requirements
  * outlier detection
* AI & machine learning > Outlier detection > add alert

# _Examples:_
## | save it -> NEW metric is exposed | Prometheus's `grafanacloud-ml-metrics`
* | Grafana sandbox,
  * [Explore > `grafanacloud-ml-metrics` > `:outlier`](https://play.grafana.org/explore?schemaVersion=1&panes=%7B%22loe%22%3A%7B%22datasource%22%3A%22grafanacloud-ml-metrics%22%2C%22queries%22%3A%5B%7B%22refId%22%3A%22A%22%2C%22expr%22%3A%22%22%2C%22range%22%3Atrue%2C%22instant%22%3Atrue%2C%22datasource%22%3A%7B%22type%22%3A%22prometheus%22%2C%22uid%22%3A%22grafanacloud-ml-metrics%22%7D%7D%5D%2C%22range%22%3A%7B%22from%22%3A%22now-1h%22%2C%22to%22%3A%22now%22%7D%2C%22compact%22%3Afalse%7D%7D&orgId=1)
## how to create outlier detection?
* Grafana cloud
  * Problems:
    * Problem1: "Not enough series: Outlier detection requires 3 or more series to work."
      * Solution: TODO:
* [Grafana sandbox](https://play.grafana.org/a/grafana-ml-app/outlier-detector)
## how to create outlier-based alert?
* Grafana cloud
  * Problems:
    * Problem1: NOT outlier detection saved
