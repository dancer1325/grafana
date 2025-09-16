* goal
  * check database / used -- by -- your Grafana instance

# requirements
* install & run Grafana
  * _Example:_ follow [Mac](../mac)

# check database / used -- by -- your Grafana instance

* ways
  * [UI](#UI)
  * [grafana.ini](#grafanaini)
  * [API](#api)

## UI

* | browser,
  * http://localhost:3000,
    * Home, Administration, General, Settings,
    * look up "database"

## grafana.ini

* | terminal,
  * `cat /opt/homebrew/etc/grafana/grafana.ini | grep -A 10 "\[database\]"`

## API

* | terminal
  * `curl -u admin:admin http://localhost:3000/api/admin/settings | grep -i database`
  * Problems:
    * Problem1: "Invalid username or password"
      * Solution: use your current password

