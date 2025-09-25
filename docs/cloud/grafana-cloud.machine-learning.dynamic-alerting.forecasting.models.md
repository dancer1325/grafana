https://grafana.com/docs/grafana-cloud/machine-learning/dynamic-alerting/forecasting/models/

* goal
  * forecast model's common fields
  * Prophet model's fields

# forecast model's common fields
## Training data range
* := how far back in time / look for training data
  * by default,
    * 90 days
  * recommendations
    * < underlying data source's retention period
      * Reason: 🧠NO data would be returned 🧠

## Training data interval
* := interval | data is trained
  * == interval | datas are taken
  * by default,
    * 5'
  * requirements
    * [100, 50,000) samples / series
      * _Example:_ 90 days / EACH 5' -> 25,920 samples

# Prophet model's fields
* [Prophet](https://github.com/facebook/prophet)
  * 's hyperparameters
    * == Prophet model's advanced configurations
    * [documentation](https://github.com/facebook/prophet/tree/main/docs)
    * [Grafana values](https://grafana.com/docs/grafana-cloud/machine-learning/dynamic-alerting/forecasting/models/)
