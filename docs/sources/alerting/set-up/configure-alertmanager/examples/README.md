* `docker compose up -d`
* localhost:3000
  * admin/admin

# built-in **Grafana Alertmanager**
* Alerts & IRM > Alerting > Settings

# Alertmanager resources
## add MORE alertmanagers
* define Prometheus AlertManager | Grafana
  * Alerts & IRM > Alerting > Settings > Add new AlertManager
    * Alertmanager
      * implementations = Prometheus
    * HTTP == http://host.docker.internal:9093/
    * Save & Test
## are managed / EACH Alertmanager
* Alerts & IRM > Alerting >
  * Contact points > Check | up right
    * resources: Contact points and notification templates
  * Notification policies > Check | up right
    * resources: Notification policies and mute timings
  * Silences > Check | up right
  * Active notifications > Check | up right
