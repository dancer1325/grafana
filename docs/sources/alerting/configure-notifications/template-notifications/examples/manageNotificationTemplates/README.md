* `docker run -p 3000:3000 --name=grafana -e "GF_AUTH_ANONYMOUS_ENABLED=true" -e "GF_AUTH_ANONYMOUS_ORG_ROLE=Admin" grafana/grafana`
* http://localhost:3000/
* Connections > Data sources > Add data source > Testdata

# Create a 
## notification template
* Alerting > Contact points > Notification template > Add notification template group
  * name: notificationtemplategroup
  * Template group
    * Add examples > choose 1 
    * save
## notification template group
* Alerting > Contact points > Notification template > Add notification template group
  * name: notificationtemplategroup
  * Template group
  ```
  {{ define "email.subject" }}
  [{{ .Status | toUpper }}] {{ .GroupLabels.alertname }} - {{ len .Alerts }} alerts
  {{ end }}
  
  {{ define "email.body" }}
  <h2>Alert Summary</h2>
  <p><strong>Status:</strong> {{ .Status }}</p>
  <p><strong>Group:</strong> {{ range .GroupLabels.SortedPairs }}{{ .Name }}={{ .Value }} {{ end }}</p>
  
  {{ if gt (len .Alerts.Firing) 0 }}
  <h3>🔥 Firing Alerts</h3>
  {{ range .Alerts.Firing }}
  <div style="border-left: 4px solid #f44336; padding: 10px; margin: 10px 0;">
    <h4>{{ .Annotations.summary }}</h4>
    <p>{{ .Annotations.description }}</p>
    <p><strong>Labels:</strong> {{ range .Labels.SortedPairs }}{{ .Name }}={{ .Value }} {{ end }}</p>
  </div>
  {{ end }}
  {{ end }}
  
  {{ if gt (len .Alerts.Resolved) 0 }}
  <h3>✅ Resolved Alerts</h3>
  {{ range .Alerts.Resolved }}
  <div style="border-left: 4px solid #4CAF50; padding: 10px; margin: 10px 0;">
    <h4>{{ .Annotations.summary }}</h4>
    <p>{{ .Annotations.description }}</p>
  </div>
  {{ end }}
  {{ end }}
  {{ end }}
  
  {{ define "slack.title" }}
  {{ .Status | toUpper }}: {{ .GroupLabels.alertname }}
  {{ end }}
  
  {{ define "slack.text" }}
  {{ range .Alerts }}
  *{{ .Annotations.summary }}*
  {{ .Annotations.description }}
  {{ end }}
  {{ end }}
  ```

# Preview a notification template
* Alerting > Contact points > Notification templates > choose 1 > 
  * Preview panel
  * Payload
    * use existing alert instance's payload
    * add custom alert instance's payload

