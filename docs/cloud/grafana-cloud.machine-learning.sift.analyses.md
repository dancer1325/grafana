https://grafana.com/docs/grafana-cloud/machine-learning/sift/analyses/

* Sift's built-in checks
  * [Error pattern logs](https://grafana.com/docs/grafana-cloud/machine-learning/sift/analyses/error-pattern-logs/)
    * responsible for
      * reviews error logs
      * highlights log patterns / increased rates | investigation time range
    * help
      * identify patterns | error logs / may indicate a problem
  * [HTTP error series](https://grafana.com/docs/grafana-cloud/machine-learning/sift/analyses/http-error-series/)
    * reviews errors |
      * HTTP request
      * HTTP response data
  * [Kube crashes](https://grafana.com/docs/grafana-cloud/machine-learning/sift/analyses/kube-crashes/)
    * review | specified namespace OR cluster,
      * pods / crashed 
        * Possible Reasons:🧠
          * application error
          * OOMKill🧠
  * Log query
    * how does it work?
      * runs a custom Loki query
      * populate a configurable template -- based on the -- result
  * Metric query
    * how does it work?
      * runs a custom Prometheus query
      * populate a configurable template -- based on the -- result 
  * TODO:

# _Example:_
## Error pattern logs
* [Grafana Sandbox](https://play.grafana.org/a/grafana-ml-app/investigations/62a81a06-4506-42a6-8bb3-2f17c0807ffc)

## HTTP error series
* [Grafana Sandbox](https://play.grafana.org/a/grafana-ml-app/investigations/3c462e14-2226-4d9b-9ecd-4e4c39a9f024)

## Kube crashes
* [Grafana Sandbox](https://play.grafana.org/a/grafana-ml-app/investigations/06a88940-7e11-4464-a8e6-62e05f270995)

## Log query
* TODO:

## Metric query
* TODO:

