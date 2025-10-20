* TODO:

# Migrate your recorded queries to Grafana-managed alert rules

* -- via -- MANUALLY

* **Administration** -> **Plugins and Data** -> **Recorded queries.**
  * write down: data source, query PromQL, interval, and time range

    ![](/grafana/media/docs/alerting/rec-query-example.png)
* **Alerting** -> **Alert rules.** > **More** -> **New Grafana recording rule**
  * Enter recording rule and metric name
    * paste PREVIOUSLY copied data
  * Define recording rule
    * paste PREVIOUSLY copied data
  * Add folder and labels
    * paste PREVIOUSLY copied data
  * Set evaluation behavior
    * paste PREVIOUSLY copied data

