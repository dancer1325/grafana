* `docker run -p 3000:3000 --name=grafana -e "GF_AUTH_ANONYMOUS_ENABLED=true" -e "GF_AUTH_ANONYMOUS_ORG_ROLE=Admin" grafana/grafana`
* http://localhost:3000/
* Connections > Data sources > Add data source > Testdata

# rules |
## DIFFERENT evaluation groups, can be evaluated SIMULTANEOUSLY
* create 2 alert rules
  * Alerting > Alert rules > New alert rule
    * alert rule1
      * name: grafanaManaged1
      * define query & alert condition
        * datasource: testdata
        * alert condition: median >90
      * folder: testdata
      * evaluation group: sameEvaluationGroup
    * alert rule2
      * name: grafanaManaged2
      * define query & alert condition
        * datasource: testdata
        * alert condition: median >50
      * folder: testdata
      * evaluation group: differentEvaluationGroup
* check state history
  * Alerting > Alert rules > Grafana-managed
    * alert rule1 > show state history
    * alert rule2 > show state history
## SAME evaluation group,
### **Grafana-managed** rules, CONCURRENTLY | DIFFERENT times
* create 2 alert rules
  * Alerting > Alert rules > New alert rule
    * alert rule1
      * name: grafanaManaged1
      * define query & alert condition
        * datasource: testdata
        * alert condition: median >90
      * folder: testdata
      * evaluation group: sameEvaluationGroup
    * alert rule2
      * name: grafanaManaged2
      * define query & alert condition
        * datasource: testdata
        * alert condition: median >50
      * folder: testdata
      * evaluation group: sameEvaluationGroup
* check state history
  * Alerting > Alert rules > Grafana-managed
    * alert rule1 > show state history
    * alert rule2 > show state history
### **Data source-managed** rules, SEQUENTIALLY
* TODO:
### **Grafana-managed rules / [imported -- from -- data source-managed rules](ref:import-ds-rules)**, SEQUENTIALLY
* TODO:
