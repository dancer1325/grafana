---
aliases:
  - ../manage-users/server-admin/
  - ../manage-users/server-admin/server-admin-manage-orgs/
  - manage-organizations/
description: Describes how to use organizations to isolate dashboard to users and
  teams.
keywords:
  - organizations
  - dashboards
labels:
  products:
    - enterprise
    - oss
menuTitle: Manage organizations
title: Manage organizations
weight: 200
---

# Manage organizations

* goal
  * organizations
    * definition
    * how to
      * create,
      * edit,
      * delete

## About organizations

* organization
  * == entity / 
    * helps you 👀isolate resources👀
  * managed by Grafana Server Administrators
  * 's goal
    * provide separate experiences | 1! Grafana instance
      * Reason:🧠MULTIPLE organizations vs MULTIPLE Grafana instances
        * easier
        * cheaper 🧠
  * 👀if you delete an organization -> deletes ALL organization's associated resources (teams, dashboards)👀
  * resources / can be shared OR isolated | BETWEEN organizations

| Resource                 | Mode                                                                 |
| ------------------------ |----------------------------------------------------------------------|
| Users                    | Share or isolate <br/> share == user belon to MULTIPLE organizations |
| Folders                  | Isolate only                                                         |
| Dashboards               | Isolate only                                                         |
| Data sources             | Isolate only                                                         |
| Alerts                   | Isolate only                                                         |
| Notification channels    | Isolate only                                                         |
| Annotations              | Isolate only                                                         |
| Reports                  | Isolate only                                                         |
| Service accounts         | Isolate only                                                         |
| Authentication providers | Share only                                                           |
| Configuration settings   | Share only                                                           |
| Licenses                 | Share                                                                |
