* `docker run -p 3000:3000 --name=grafana -e "GF_AUTH_ANONYMOUS_ENABLED=true" -e "GF_AUTH_ANONYMOUS_ORG_ROLE=Admin" grafana/grafana`
* http://localhost:3000/
* Connections > Data sources > Add data source > Testdata

# tree structure
## root == Default notification policy
* Alerting > Notification policies > Default policy >
  * ONLY create Default policy's child policies

## child policies
* Alerting > Notification policies > New child policy > 
  * `key1:value1`

## sibling policies
* Alerting > Notification policies > PREVIOUS child policy > New child policy >
  * sibling
    * based on how to evaluate | policy tree -> ABOVE or BELOW
  * subchild
