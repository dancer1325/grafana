# ALLOW override options
* [Grafana playground](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser&editPanel=1)
  * ADD field override
## Fields with name
* [Grafana playground](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser&editPanel=1)
  * see EXISTING overrides
## Field with name matching regex
* [Grafana playground](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser&editPanel=1)
* Add field override > Field with name matching regex > `/.*02/` **Graph styles > Transform** > Negative
  * see how "backend_02" is selected properly
## Fields with type
* [Grafana playground](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser&editPanel=1)
* Add field override > Fields with type > Number > **Graph styles > Transform** > Negative
  * see how "backend_01" & "backend_02" are inverted
## Fields returned by query
* [Grafana playground](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser&editPanel=1)
* Add field override > Fields returned by query > A > **Graph styles > Transform** > Negative
  * see how queryA is inverted
## Fields with values
* [Grafana playground](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=now-1h&to=now&timezone=browser&editPanel=1)
* Add field override > Fields returned with values > First >+ 40 > **Graph styles > Transform** > Negative
  * see how defined reducer condition values are inverted
