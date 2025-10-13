* [Grafana playground](https://play.grafana.org/d/KIhkVD6Gk/gauges?orgId=1&from=now-6h&to=now&timezone=utc&refresh=10s)

# uses
## CPU consumption & RAM availability
* [Grafana plaground](https://play.grafana.org/d/KIhkVD6Gk/gauges?orgId=1&from=now-6h&to=now&timezone=utc&refresh=10s&editPanel=12)
## Service level objectives (SLOs)
* TODO:

# Supported data formats
## 1! value
* [Grafana playground](https://play.grafana.org/d/KIhkVD6Gk/gauges?orgId=1&from=now-6h&to=now&timezone=utc&refresh=10s&editPanel=12)
  * Queries > 
    * remove ALL, EXCEPT to queryA
    * queryA > 1! serie
### ALTHOUGH you ONLY have 1 value & want to define a minimum and maximum -> set them manually | [Standard options](#standard-options)
* [Grafana playground](https://play.grafana.org/d/KIhkVD6Gk/gauges?orgId=1&from=now-6h&to=now&timezone=utc&refresh=10s&editPanel=12)
  * Standard Options > set minimum & maximum
## 1 row / MULTIPLE values
* [Grafana playground](https://play.grafana.org/d/KIhkVD6Gk/gauges?orgId=1&from=now-6h&to=now&timezone=utc&refresh=10s&showCategory=Standard%20options&editPanel=12)
  * Standard Options > Min & Max
    * adjust the values & check how the shadow & compared percentage
    * you can see easily -- via -- Gauge > Show threshold labels
## ALL values
* [Grafana playground](https://play.grafana.org/d/KIhkVD6Gk/gauges?orgId=1&from=now-6h&to=now&timezone=utc&refresh=10s&showCategory=Standard%20options&editPanel=12)
  * Value options > Show > All values

# Value options
* [Grafana plaground](https://play.grafana.org/d/KIhkVD6Gk/gauges?orgId=1&from=now-6h&to=now&timezone=utc&refresh=10s&editPanel=12)
  * Value options
    * switch BETWEEN the values
