* goal
  * check Grafana's 
    * configuration file's location
    * plugin's location
    * data base's location
  * back up grafana

## Prequisites

* install [Docker](https://docs.docker.com/install/)
* `docker run -d --name grafana -p 3000:3000 grafana/grafana`

## Grafana's configuration file's location
* steps
  * `docker exec -it --user root grafana sh`
  * `cat $WORKING_DIR/defaults.ini`

## Grafana's plugin's location
* steps
  * `docker exec -it --user root grafana sh`
  * `cd $WORKING_DIR/data/plugins`

## Grafana's database's location
* steps
  * `docker exec -it --user root grafana sh`
  * `cat $WORKING_DIR/data/grafana.db`
