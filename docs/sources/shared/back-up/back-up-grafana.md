---
headless: true
labels:
  products:
    - enterprise
    - oss
title: Back up Grafana
---

# Back up Grafana

* goal  
  * how to back up a local Grafana deployment (configuration, plugin data, & Grafana database)

## Back up the Grafana configuration file

* Grafana configuration files
  * location 
    * |
      * default one
        * `$WORKING_DIR/defaults.ini`
        * if you used `deb` OR `rpm` packages -> `/etc/grafana/grafana.ini`
      * custom one
        * `$WORKING_DIR/custom.ini` 
    * [how to configure](https://grafana.com/docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#configuration-file-location)

* steps
  * copy & paste

## Back up plugin data

* Grafana plugin files
  * location
    * default one
      * `$WORKING_DIR/data/plugins`
      * if you used `deb` OR `rpm` packages -> `/var/lib/grafana/plugins`
    * specified | Grafana init.d script -- via -- `--config`

* steps
  * copy & paste

## Back up the Grafana database

* pros
  * roll back -- to a -- previous version

### SQLite

* == 💡default Grafana database💡

* SQLite database
  * == 👀1! file | disk👀
  * location
    * default one
      * `$WORKING_DIR/data/grafana.db`
      * if you used `deb` OR `rpm` packages -> `/var/lib/grafana/grafana.db`
    * specified | Grafana init.d script -- via -- `--config`

* steps
  * shut down Grafana
  * copy & paste

### MySQL

* TODO: To back up or restore a MySQL Grafana database, run the following commands:

```bash
backup:
> mysqldump -u root -p[root_password] [grafana] > grafana_backup.sql

restore:
> mysql -u root -p grafana < grafana_backup.sql
```

### Postgres

To back up or restore a Postgres Grafana database, run the following commands:

```bash
backup:
> pg_dump grafana > grafana_backup

restore:
> psql grafana < grafana_backup
```
