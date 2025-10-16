* `docker run -d -p 3000:3000 grafana/grafana`
* http://localhost:3000/
  * admin / admin

## Saved queries
### requirements
#### | Grafana OSS, ❌NOT displayed❌
* Explore > choose a datasource
#### | Grafana Cloud
* Create account
* Grafana Cloud portal > Launch instance > Explore > "grafanacloud-usage" > `grafanacloud_grafana_instance_active_users`
  * [example](https://alfredotic0809.grafana.net/explore?schemaVersion=1&panes=%7B%223la%22%3A%7B%22datasource%22%3A%22grafanacloud-ngalertmanager%22%2C%22queries%22%3A%5B%7B%22refId%22%3A%22A%22%2C%22datasource%22%3A%7B%22type%22%3A%22alertmanager%22%2C%22uid%22%3A%22grafanacloud-ngalertmanager%22%7D%7D%5D%2C%22range%22%3A%7B%22from%22%3A%22now-1h%22%2C%22to%22%3A%22now%22%7D%2C%22compact%22%3Afalse%7D%7D&orgId=1)
### Steps to create
* Explore > Choose datasource > run query > save query
### **Saved queries** drawer
* Explore > Add from saved queries
#### if you filter by MULTIPLE
* create MULTIPLE saved queries / DIFFERENT tags
##### datasource -> `OR` operator
* my Grafana Cloud
##### user name -> `OR` operator
* my Grafana Cloud
##### tag -> `AND` operator
* my Grafana Cloud

# Add a query
* [here](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=2025-10-10T08:47:44.693Z&to=2025-10-10T09:47:44.693Z&timezone=browser&editPanel=1)
## **Add query** by yourself
* Data source > prometheus.. > type some metric > run queries
## **Add from saved queries**
* my Grafana cloud
## **Replace EXISTING query -- with -- saved query**
* my Grafana cloud


# Query options
## Relative time override dashboard time picker
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Time series
  * Relative time: 3h
  * Save dashboard
  * Adjust Dashboard's date time picker
## Time shift, shift panel's time begining -- relative to -- dashboard's time picker
* **Dashboards** > **New** > **Add visualization** >
  * Visualization = Time series
  * Time shift: 1h
  * Save dashboard
