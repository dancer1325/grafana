---
aliases:
  - ../install/
  - ../installation/
  - ../installation/installation/
  - ../installation/requirements/
  - /docs/grafana/v2.1/installation/install/
  - ./installation/rpm/
description: Installation guide for Grafana
labels:
  products:
    - enterprise
    - oss
title: Install Grafana
weight: 100
---

# Install Grafana

* requirements
  * supported 
    * OS
    * hardware / >= minimum requirements
    * database
    * browser

* [youtube video](https://www.youtube.com/watch?v=f-x_p2lvz8s)
  * install Grafana | various OS
  * TODO:

## Supported operating systems

- [Debian or Ubuntu](debian/)
- [RHEL or Fedora](redhat-rhel-fedora/)
- [SUSE or openSUSE](suse-opensuse/)
- [macOS](mac/)
- [Windows](windows/)

## Hardware recommendations

- Minimum recommended memory: 512 MB
- Minimum recommended CPU: 1 core

* features / might require > memory or CPUs
- [Alerting](/grafana/docs/sources/alerting)
- [Data source proxy](/grafana/docs/sources/developers/http_api/data_source.md)

## Supported databases

* Grafana
  * ⚠️requires a database⚠️ 
    * | store
      * its configuration data (users, data sources, and dashboards)
    * /
      * requirements -- depend on --
        * Grafana installation size
        * features / you use
    * supported
      - [SQLite 3](https://www.sqlite.org/index.html)
        - default one
        - stored | Grafana installation location
        - use cases
          - environment is small
          - [SQLite documentation](https://www.sqlite.org/whentouse.html)
      - [MySQL 8.0+](https://www.mysql.com/support/supportedplatforms/database.html)
        - allows
          - [high availability](../set-up-for-high-availability)
        - bugs
          - read-only MySQL servers
      - [PostgreSQL 12+](https://www.postgresql.org/support/versioning/)
        - allows
          - [high availability](../set-up-for-high-availability)
        - versions / [bug prevents using Grafana](https://www.postgresql.org/message-id/flat/15865-17940eacc8f8b081%40postgresql.org)
          - 10.9, 
          - 11.4,
          - 12-beta2
    * [how to configure database | `grafana.ini`](../configure-grafana/_index.md#database) 

* Grafana binaries & images /
  * built | unsupported databases,
    * might NOT work
  * built with [BoringCrypto](https://pkg.go.dev/crypto/internal/boring)
    * may have problems

## Supported web browsers

* requirements
  * enable JavaScript | your browser

* supported browser's latest versions
  - Chrome/Chromium
  - Firefox
  - Safari
  - Microsoft Edge
