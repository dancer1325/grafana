* `docker run -p 3000:3000 --name=grafana -e "GF_AUTH_ANONYMOUS_ENABLED=true" -e "GF_AUTH_ANONYMOUS_ORG_ROLE=Admin" grafana/grafana`
* http://localhost:3000/
* Connections > Data sources > Add data source > Testdata

# Select a notification template / contact point
* Alerting > Contact points > choose 1 > Optional email settings > click some field / can be templated > edit
  * TODO:
