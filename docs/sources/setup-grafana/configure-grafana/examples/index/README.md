# Configuration file location
## `$WORKING_DIR/conf/defaults.ini` OR `<WORKING DIRECTORY>/conf/defaults.ini`
* `docker run -d --name=grafana -p 3000:3000 grafana/grafana-oss:main-ubuntu`
* `docker exec -it grafana cat conf/defaults.ini`
* see [defaults.ini](defaults.ini)
## (`$WORKING_DIR/conf/custom.ini` OR `<WORKING DIRECTORY>/conf/custom.ini`) OR `/usr/local/etc/grafana/grafana.ini`
* `docker compose up -d`
* http://localhost:3000/
  * admin/mypassword

# comments | ".ini" files
* [grafana.ini](grafana.ini)
* `docker compose up -d`
* `docker exec -it grafana cat /etc/grafana/grafana.ini`

# Override configuration with environment variables
* `docker compose up -d`
* http://localhost:3000/profile
  * admin/mypassword
  * check the email: bb@a.com

# Variable expansion
## `env` provider
* `docker compose up -d`
* http://localhost:3000/admin/settings
  * check `instance_name:	alfred`

## `file` provider

## `vault` provider
* TODO:

# Configuration options
## `app_mode`
### `production`  ==  default one
* `docker compose up -d`
* http://localhost:3000/admin/settings
  * check `app_mode:production`
### `development`
* `docker compose up -d`
* http://localhost:3000/admin/settings
  * check `app_mode:development`
## `instance_name`
* `docker compose up -d`
* http://localhost:3000/admin/settings
  * check `instance_name`
## `[paths]`
* `mkdir ./grafana-local/`
* `sudo chmod -R 777 ./grafana-local/`
* `docker compose up -d`
  * Problems:
    * Problem1: " level=error msg="alert migration failure: could not get migration log" error="failed to check table existence: unable to open database file: permission denied"
      * Workaround: Comment bind mounts
      * Solution: TODO:
* http://localhost:3000/admin/settings
  * check paths
### `data`
* `docker exec -it grafana sh -c "cd /var/lib/grafana && ls -la"`
### `logs`
* `docker exec -it grafana sh -c "cd /var/log/grafana"`
  * Problems:
    * Problem1: Why is there NO entry?
      * Solution: TODO:
### `plugins`
#### path / scan
* `docker exec -it grafana sh -c "cd /var/lib/grafana/plugins && ls -la"`
  * path / Grafana scans
#### built-in plugins | /usr/share/grafana/public
* `docker exec -it grafana sh -c "cd /usr/share/grafana/public && ls -la"`
### TODO:

## TODO:

## `[explore]`
### `enabled`
* `docker compose up -d`
* http://localhost:3000
  * Explore section NOT appear
### `defaultTimeOffset`
* `docker compose up -d`
* http://localhost:3000
  * Explore
    * Problems: 
      * Problem1: Why does it appear 1 hour?
        * Solution: TODO:

