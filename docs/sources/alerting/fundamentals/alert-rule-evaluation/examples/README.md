* `docker run -p 3000:3000 --name=grafana -e "GF_AUTH_ANONYMOUS_ENABLED=true" -e "GF_AUTH_ANONYMOUS_ORG_ROLE=Admin" grafana/grafana`
* http://localhost:3000/
* Connections > Data sources > Add data source > Testdata

# Alerting lifecycle
* TODO:

# Notification routing
* TODO:

# Evaluation group
## EVERY alert rule & recording rule is assigned -- to an -- evaluation group
* Alerting > 
  * Alert rules > 
    * New alert rule > evaluation group: required
    * New recording rule > evaluation group: required
## evaluation interval
### EXIST evaluation interval / EACH evaluation group
* Alerting > Alert rules > New alert rule > 
  * name: test
  * define query:
    * expression: Random Walk
    * alert condition: Median 50
  * Add folder and labels
    * folder: testData
  * Set evaluation behavior > New evaluation group
    * name: evaluationGroupWithInterval
    * evaluation interval: choose whatever you want
###  == how frequently the alert rule is checked
* Alerting > Alert rules > choose alert > show state history

# Pending period
* Alerting > Alert rules > New alert rule >
  * name: pendingPeriod
  * Define query and alert condition
    * Scenario: CSV Metric values
    * String input: 1,20,90,30,5,0,80
    * Alert condition: Last is above 70
  * Add folder and labels
    * folder: pendingPeriod
  * Set evaluation behavior
    * name: pendingPeriod
    * evaluation interval: 1m
    * pending period: 20s
## how long the condition MUST be met -- to -- trigger the alert rule 
* Alerting > Alert rules > show state history 
## \> evaluation interval
* [follow](#exist-evaluation-interval--each-evaluation-group)
## if you set **Pending period=0** -> skip the **Pending** state
* Alerting > Alert rules > edit alert rule > Pending period:0s
* Alerting > Alert rules > show state history
## **Normal** -> **Pending** -> **Alerting**
* Alerting > Alert rules > show state history

# Keep firing for
## AFTER **Keep firing for** period WITHOUT meeting alert rule's condition -> alert transitions -- to the -- **Normal** state & marked as **Resolved**
* TODO:
## if **Keep firing for** period == 0 -> transition -- DIRECTLY to -- Normal
* TODO:
