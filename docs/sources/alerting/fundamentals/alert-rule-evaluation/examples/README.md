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
## TODO:
## \> evaluation interval
* [follow](#exist-evaluation-interval--each-evaluation-group)
## TODO:

# Keep firing for
