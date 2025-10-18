* `docker run -p 3000:3000 --name=grafana -e "GF_AUTH_ANONYMOUS_ENABLED=true" -e "GF_AUTH_ANONYMOUS_ORG_ROLE=Admin" grafana/grafana`
* http://localhost:3000/
* Connections > Data sources > Add data source > Testdata

# Alert instances OR Alerts
## EACH alert rule can produce >= 1 alert instances
* Alerting > Alert rules > 
  * New alert rule >
    * name: alertInstance
    * Define query and alert condition
      * Scenario: Random WALK
      * Series count: 03
      * Alert condition: Last is above 70
    * Add folder and labels
      * folder: pendingPeriod
    * Set evaluation behavior
      * Evaluation group
        * name: alertInstances
        * evaluation interval: 10s
      * Pending period: 0
      * keep firing for: 0
  * alertInstances > View > Instances: 3
