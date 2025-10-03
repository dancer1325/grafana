---
aliases:
  - ../../http_api/other/
canonical: /docs/grafana/latest/developers/http_api/other/
description: Grafana Other HTTP API
keywords:
  - grafana
  - http
  - documentation
  - api
  - other
labels:
  products:
    - enterprise
    - oss
title: 'Other HTTP API '
---

# Frontend Settings API

## `GET /api/frontend/settings`
* get Settings
* 's request
  ```
  Accept: application/json
  Content-Type: application/json
  Authorization: Bearer eyJrIjoiT0tTcG1pUlY2RnVKZTFVaDFsNFZXdE9ZWmNrMkZYbk
  ```
  * Bearer Token:
    * Problems:
      * Problem1: how to get?
        * Attempt1: Grafana UI > Administration > Authentication
        * Solution: TODO: 

# Login API

## `GET /api/login/ping`
* allows
  * renew -- , based on remember cookie, -- session 
* 's request
  ```
  Accept: application/json
  Content-Type: application/json
  Authorization: Bearer eyJrIjoiT0tTcG1pUlY2RnVKZTFVaDFsNFZXdE9ZWmNrMkZYbk
  ```

* 's return
  * `message`

# Health API

## `GET /api/health`
* 's return
  * Grafana's health information 
* 's response
  * `commit`
  * `database`
  * `version`
