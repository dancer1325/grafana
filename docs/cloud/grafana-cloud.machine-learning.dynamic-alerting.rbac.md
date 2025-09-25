https://grafana.com/docs/grafana-cloud/machine-learning/dynamic-alerting/rbac/

* Dynamic Alerting creation & management permissions
  * 👀configurable -- through the -- Grafana Cloud's [RBAC](https://grafana.com/docs/grafana/latest/administration/roles-and-permissions/access-control/plan-rbac-rollout-strategy/)👀
  * ML-plugin 
    * specific RBAC roles
      * ML Editors
        * create/edit/delete
          * forecasts
          * outlier detectors
          * holidays
      * ML Viewers
        * view
          * forecasts
          * outlier detectors
    * [how to give rights](https://youtu.be/-zNoEOvlkYc?si=z0F1Ej6WnZwZwrFS)
      * steps
        * Administration > Users and access > Users
        * check the user
        * Plugin roles > Grafana AI/ML > ML Editor/ML Viewer

# _Examples:_
## requirements
* [Grafana sandbox](https://play.grafana.org/admin/plugins)
  * ❌NOT ALLOWED ❌
* Grafana cloud
  * TODO: set it up
## how to give rights?
* 
