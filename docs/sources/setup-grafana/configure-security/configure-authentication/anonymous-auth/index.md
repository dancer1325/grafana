---
aliases:
  - ../../../auth/anonymous-auth/
description: Learn how to configure anonymous access in Grafana
labels:
  products:
    - enterprise
    - oss
menuTitle: Anonymous access
title: Configure anonymous access
weight: 250
---

# Anonymous authentication

* allows
  * Grafana accessible WITHOUT login

* | Grafana Enterprise,
  * anonymous users' pricing == active users' pricing

## Before you begin

* permissions `users:read`
  * audience
    * server admins
  * allow
    * read users & devices tab

## Anonymous devices

* anonymous devices
  * allows
    * managing & monitoring anonymous access

* steps
  * **Administration > Users**

* | Grafana v10.2, 10.3, 10.4,
  * if you want to display anonymous users & devices ->

    ```bash
    [feature_toggles]
    enable = displayAnonymousStats
    ```

## Configuration

```bash
[auth.anonymous]
enabled = true

# Organization name / used for unauthenticated users
org_name = Main Org.

# unauthenticated users' role
# ALLOWED values: `Editor`, `Viewer` and `Admin`
org_role = Viewer

# hide the Grafana version text | footer & help tooltip / unauthenticated users
# by default, false
hide_version = true

# limits the number of anonymous devices | your Grafana instance
# AFTER reaching the limit, NEW anonymous devices will be denied access
device_limit =
```
