# Grafana Drilldown apps
## Logs Drilldown
* [Grafana playground > Drilldown > Logs](https://play.grafana.org/a/grafana-lokiexplore-app/explore?patterns=%5B%5D&from=now-15m&to=now&timezone=utc&var-lineFormat=&var-ds=grafanacloud-logs&var-filters=&var-fields=&var-levels=&var-metadata=&var-jsonFields=&var-all-fields=&var-patterns=&var-lineFilterV2=&var-lineFilters=&var-primary_label=service_name%7C%3D~%7C.%2B)
  * query & visualizations ALREADY set up
  * "show logs"
    * Reason:🧠check used query🧠

## Metrics Drilldown
* [Grafana playground > Drilldown > Metrics](https://play.grafana.org/a/grafana-metricsdrilldown-app/drilldown?layout=grid&filters-rule=&filters-prefix=&filters-suffix=&from=now-1h&to=now&timezone=utc&var-ds=grafanacloud-demoinfra-prom&var-filters=&from-2=now-1h&to-2=now&timezone-2=utc&var-labelsWingman=%28none%29&search_txt=&var-metrics-reducer-sort-by=default&var-other_metric_filters=)
  * query & visualizations ALREADY set up
  * "select" > "explore"
    * Reason:🧠check used query🧠

## Trace Drilldown
* [Grafana playground > Drilldown > Trace](https://play.grafana.org/a/grafana-exploretraces-app/explore?from=now-30m&to=now&timezone=utc&var-ds=grafanacloud-demoinfra-traces&var-primarySignal=nestedSetParent%3C0&var-filters=&var-metric=rate&var-groupBy=resource.service.name&var-spanListColumns=&var-latencyThreshold=&var-partialLatencyThreshold=&actionView=breakdown)
  * TODO:

## Profiles Drilldown
* [Grafana playground > Drilldown > Profiles](https://play.grafana.org/a/grafana-pyroscope-app/explore?searchText=&panelType=time-series&layout=grid&hideNoData=off&explorationType=all&var-serviceName=ebpf&var-profileMetricId=process_cpu:cpu:nanoseconds:cpu:nanoseconds&var-spanSelector=undefined&var-dataSource=grafanacloud-profiles&var-filters=&var-filtersBaseline=&var-filtersComparison=&var-groupBy=)
  * "explore"
    * Reason:🧠check used query🧠
