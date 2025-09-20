* goal
  * save Grafana's data
  * configure Grafana -- via -- environment variables
  * TODO:

## Prequisites

* install [Docker](https://docs.docker.com/install/)

## Save Grafana's data
### -- via -- Docker volumes
* steps
  * `docker volume create grafana-storage`
  * `docker volume inspect grafana-storage`
  *  
    ```
    docker run -d -p 3000:3000 --name=grafana \
      --volume grafana-storage:/var/lib/grafana \
      grafana/grafana-enterprise
    ```
  * check anything created is persisted
    * | browser,
      * http://localhost:3000/, admin/admin
      * dashboard, new, create & save something
    * `docker stop grafana` & `docker rm grafana`
    *
      ```
      docker run -d -p 3000:3000 --name=grafana \
        --volume grafana-storage:/var/lib/grafana \
        grafana/grafana-enterprise
      ```
    * | browser,
      * http://localhost:3000/, admin/admin
      * dashboard, check exist PREVIOUSLY created dashboard
  
### -- via -- bind mounts
* steps
  * `mkdir data`
  * 
    ```
    docker run -d -p 3000:3000 --name=grafana \
      --user "$(id -u)" \
      --volume "$PWD/data:/var/lib/grafana" \
      grafana/grafana-enterprise
    ```
  * check anything created is persisted
    * | browser,
      * http://localhost:3000/, admin/admin
      * dashboard, new, create & save something
    * `docker stop grafana` & `docker rm grafana`
    *
      ```
      docker run -d -p 3000:3000 --name=grafana \
        --user "$(id -u)" \
        --volume "$PWD/data:/var/lib/grafana" \
        grafana/grafana-enterprise
      ```
  * | browser,
    * http://localhost:3000/, admin/admin
    * dashboard, check exist PREVIOUSLY created dashboard
  


## configure Grafana -- via -- environment variables

* steps
  *
    ```
    docker run -d -p 3000:3000 --name=grafana \
      -e "GF_LOG_LEVEL=debug" \
      grafana/grafana-enterprise
    ```
  * check logs / `debug` level appear
