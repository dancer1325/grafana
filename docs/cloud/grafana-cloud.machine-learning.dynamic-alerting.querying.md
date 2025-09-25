https://grafana.com/docs/grafana-cloud/machine-learning/dynamic-alerting/querying/

* `grafanacloud-ml-metrics`
  * == Prometheus data source
    * allows
      * be querying -- via -- PromQL
  * requirements
    * Grafana Cloud
    * ⚠️train a forecast⚠️
      * -> ALL available series' resolution == forecast's training data interval 
  * uses
    * translate specific queries -- into -- running forecasts

* main metrics / query
  * `<forecast_metric_name>:predicted`
    * provides
      * series -- related to the -- specific forecast's predictions 
  * `<forecast_metric_name>:actual`
    * provides
      * current values -- retrieved from the -- forecast query

* `:predicted`
  * == metric /
    * [documentation](https://github.com/facebook/prophet/blob/main/docs/_docs/quick_start.md?plain=1#L170)
    * 's ALLOWED series -- depend on -- `ml_forecast`

* `:actual`
  * == metric / 
    * allows
      * querying the datasource TILL up-to-date data
  * if you want to compare vs `:predicted` -> use `ignoring (ml_forecast)`
    * Reason:🧠query's results do NOT have an `ml_forecast` label🧠
 
* `:anomalous`
  * == anomaly detection
  * == metric /
    * := `:actual` != [`:predicted` lower bound, `:predicted` upper bound]
    * if `:actual` 
      * = 1 == anomalously high 
      * = 0 == NOT anomalous
      * = -1 == anomalously low
  * if you want to 
    * query ALL points | there are anomalies (high or low) -> query for `:anomalous != 0`
    * compare vs `:predicted` OR `:actual` -> use `ignoring (ml_forecast)`
      * Reason:🧠query's results do NOT have an `ml_forecast` label🧠

# _Examples:_
* steps
  * [Grafana sandbox > explore > grafanacloud-ml-metric](https://play.grafana.org/explore?schemaVersion=1&panes=%7B%22wcg%22%3A%7B%22datasource%22%3A%22grafanacloud-ml-metrics%22%2C%22queries%22%3A%5B%7B%22refId%22%3A%22A%22%2C%22expr%22%3A%22%22%2C%22range%22%3Atrue%2C%22instant%22%3Atrue%2C%22datasource%22%3A%7B%22type%22%3A%22prometheus%22%2C%22uid%22%3A%22grafanacloud-ml-metrics%22%7D%7D%5D%2C%22range%22%3A%7B%22from%22%3A%22now-1h%22%2C%22to%22%3A%22now%22%7D%2C%22compact%22%3Afalse%7D%7D&orgId=1)
  * code
    * != builder
    * Reason:🧠copy & paste the queries🧠
## `:predicted`
* steps
  * `sample_forecast:predicted`

## `:actual`
* steps
  * `sample_forecast:actual`
  * `abs(sample_forecast:predicted{ml_forecast="yhat"} - ignoring (ml_forecast) sample_forecast:actual)`

## Querying the Values of Anomalous Points
* steps
  * 
    ```
    # query anomalous values
    sample_forecast:actual and ignoring (ml_forecast) (sample_forecast:anomalous != 0)
    
    # query anomalous values < lower bound
    sample_forecast:actual and ignoring (ml_forecast) (sample_forecast:anomalous == -1)
    # OR
    sample_forecast:actual < ignoring (ml_forecast) sample_forecast:predicted{ml_forecast="yhat_lower"}
    
    # query anomalous values > upper bound
    sample_forecast:actual and ignoring (ml_forecast) (sample_forecast:anomalous == 1)
    # OR
    sample_forecast:actual > ignoring (ml_forecast) sample_forecast:predicted{ml_forecast="yhat_upper"}
    ```
