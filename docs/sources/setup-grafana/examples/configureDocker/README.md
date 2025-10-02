* goal
  * configure Docker

# Supported Docker image variants
## Alpine image
* `docker run -d --name=grafana -p 3000:3000 grafana/grafana:main`
* clean ALL
  * `docker kill grafana`
  * `docker container prune`

## Ubuntu image
* `docker run -d --name=grafana -p 3000:3000 grafana/grafana:main-ubuntu`
* clean ALL
  * `docker kill grafana`
  * `docker container prune`

### Enterprise
* `docker run -d --name=grafana -p 3000:3000 grafana/grafana-enterprise:main-ubuntu`
* clean ALL
  * `docker kill grafana`
  * `docker container prune`

### Open Source
* `docker run -d --name=grafana -p 3000:3000 grafana/grafana-oss:main-ubuntu`
* clean ALL
  * `docker kill grafana`
  * `docker container prune`

## specific Grafana version
* _Example:_
  * `docker run -d -p 3000:3000 --name grafana grafana/grafana-enterprise:9.4.7`

# Run Grafana | main branch
* TODO:

# default paths
* `docker run -d --name=grafana -p 3000:3000 grafana/grafana-oss:main-ubuntu`
* `docker inspect grafana | grep -A 20 "Env"`
* `docker exec -it grafana cat /etc/grafana/grafana.ini`

# install plugins -- from -- other sources
* 
  ```bash
  docker run -d -p 3000:3000 --name=grafana \
  -e "GF_INSTALL_PLUGINS=https://github.com/grafana/piechart-panel/releases/download/v1.6.2/grafana-piechart-panel-1.6.2.zip;grafana-piechart-panel" \
  grafana/grafana-enterprise:9.5.0
  ```
  * Problems:
    * Problem1: 
      * Attempt1: 
        ```bash
          docker run -d -p 3000:3000 --name=grafana \
          -e "GF_PLUGIN_ALLOW_LOADING_UNSIGNED_PLUGINS=true" \
          -e "GF_INSTALL_PLUGINS_HTTP_TIMEOUT=120" \
          -e "GF_INSTALL_PLUGINS=https://github.com/grafana/piechart-panel/releases/download/v1.6.2/grafana-piechart-panel-1.6.2.zip;grafana-piechart-panel" \
          grafana/grafana-enterprise:9.5.0
        ```
      * Solution: TODO:

# build a custom Grafana Docker image
* | [this path](/grafana/packaging/docker/custom)
  
  ```bash
  # build the Docker image
  docker build \
    --build-arg "GRAFANA_VERSION=latest-ubuntu" \
    -t grafana-custom .
  
  # run the custom grafana container
  docker run -d -p 3000:3000 --name=grafana grafana-custom
  ```

* TODO:

# Logging

* `docker run -p 3000:3000 --name=grafana -e "GF_LOG_MODE=console file" grafana/grafana`
  * Docker container logs are forwarded | 
    * console | you run the own Docker container
      * check the logging
    * Docker container's "/var/log/grafana/grafana.log"
      * `docker exec grafana cat /var/log/grafana/grafana.log`
        * check the logs
      * `docker inspect grafana | grep -A 20 "Env"`
        * check the environment variable `GF_PATHS_LOGS`

# Configure Grafana with Docker Secrets OR Docker volumes

## -- via -- Docker Secrets
### _Example:_ Amazon CloudWatch 
* [Amazon CloudWatch datasource](../../../datasources/aws-cloudwatch)
* TODO:
* To configure the data source, you must provide information such as the AWS ID-Key, secret access key, region, and so on
* You can use Docker secrets as a way to provide this information.

Example:

The example below shows how to use Grafana environment variables via Docker Secrets for the AWS ID-Key, secret access key, region, and profile.

The example uses the following values for the AWS Cloudwatch data source:

```bash
AWS_default_ACCESS_KEY_ID=aws01us02
AWS_default_SECRET_ACCESS_KEY=topsecret9b78c6
AWS_default_REGION=us-east-1
```

1. Create a Docker secret for each of the values noted above.

   ```bash
   echo "aws01us02" | docker secret create aws_access_key_id -
   ```

   ```bash
   echo "topsecret9b78c6" | docker secret create aws_secret_access_key -
   ```

   ```bash
   echo "us-east-1" | docker secret create aws_region -
   ```

1. Run the following command to determine that the secrets were created.

   ```bash
   $ docker secret ls
   ```

   The output from the command should look similar to the following:

   ```
   ID                          NAME           DRIVER    CREATED              UPDATED
   i4g62kyuy80lnti5d05oqzgwh   aws_access_key_id             5 minutes ago        5 minutes ago
   uegit5plcwodp57fxbqbnke7h   aws_secret_access_key         3 minutes ago        3 minutes ago
   fxbqbnke7hplcwodp57fuegit   aws_region                    About a minute ago   About a minute ago
   ```

   Where:

   ID = the secret unique ID that will be use in the docker run command

   NAME = the logical name defined for each secret

1. Add the secrets to the command line when you run Docker.

   ```bash
   docker run -d -p 3000:3000 --name grafana \
     -e "GF_DEFAULT_INSTANCE_NAME=my-grafana" \
     -e "GF_AWS_PROFILES=default" \
     -e "GF_AWS_default_ACCESS_KEY_ID__FILE=/run/secrets/aws_access_key_id" \
     -e "GF_AWS_default_SECRET_ACCESS_KEY__FILE=/run/secrets/aws_secret_access_key" \
     -e "GF_AWS_default_REGION__FILE=/run/secrets/aws_region" \
     -v grafana-data:/var/lib/grafana \
     grafana/grafana-enterprise
   ```

You can also specify multiple profiles to `GF_AWS_PROFILES` (for example, `GF_AWS_PROFILES=default another`).

The following list includes the supported environment variables:

- `GF_AWS_${profile}_ACCESS_KEY_ID`: AWS access key ID (required).
- `GF_AWS_${profile}_SECRET_ACCESS_KEY`: AWS secret access key (required).
- `GF_AWS_${profile}_REGION`: AWS region (optional).

## -- via -- Docker volumes
* | this path,
  * `docker compose up`
* | browser,
  * http://localhost:3000/
    * "admin" / "admin"
    * "admin" / "mysecretpassword"
    * Problems: 
      * Problem1: "401"
        * Attempt1: -- via -- volume
        * Attempt2: pass directly environment variable
        * Solution: TODO:

# Troubleshoot a docker deployment

## -- via -- Docker CLI
* | any terminal,
  * `docker run -p 3000:3000 --name=grafana -e "GF_LOG_LEVEL=debug" grafana/grafana`
    * check ALSO level=debug

## -- via -- Docker Compose
* | this path
  * `docker compose up`
    * check ALSO level=debug

## validate Docker compose file
* | this path,
  * `docker compose config`

