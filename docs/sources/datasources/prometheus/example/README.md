* `docker run -d -p 3000:3000 grafana/grafana`

# Grafana provides native support for Prometheus
* http://localhost:3000/
  * Connections > Data sources > Add data source
  * Prometheus already installed

# Exemplars
* TODO:

# Grafana metrics | Prometheus
## exposes metrics -- for -- Prometheus | `/metrics` endpoint
* localhost:3000/metrics
## includes a pre-built dashboard
* Dashboard > Create dashboard > Add visualization > data source == Dashboard
  * Grafana time series visualization 

  ![](grafanaBuiltInDashboard.gif)
