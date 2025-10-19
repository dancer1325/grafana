* `docker run -d -p 3000:3000 grafana/grafana`
* localhost:3000
  * admin/admin
  * Connections > Data sources > Add data source > Testdata
  * Alerting > Alert rules > New alert rule >
    * name: test
    * define query:
      * Scenario: CSV Metric Values
      * String Input: 1,20,90,30,5,0,120
      * alert condition: Last above 50
    * Add folder and labels
      * folder: silence
      * labels
        * `key1=value1`
    * Set evaluation behavior > New evaluation group
      * name: silence
      * evaluation interval: choose whatever you want

# Add silence
* Alerting > Silences > Add silence > 
  * Alertmanager: built-in Grafana Alertmanager
  * establish start & end
  * `key1=value1`
* Alerting > Active notifications
  * notification's status = supressed
