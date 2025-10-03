---
aliases:
  - ../../../auth/grafana/
description: Learn how to configure basic authentication in Grafana
labels:
  products:
    - enterprise
    - oss
menuTitle: Basic auth
title: Configure basic authentication
weight: 200
---

# Configure basic authentication

* Grafana basic authentication
  * by default, enabled 

## Disable basic authentication

```bash
[auth.basic]
enabled = false
```
* uses
  * private endpoints
* ❌NOT affect❌
  * web login

## Password policy

* requirements
  * \>=4  characters

* `password_policy`
  * configuration option /
    * stronger password policy
  * uses | 
    * new
    * updated passwords
  * ❌NOT uses❌
    * passwords / NOT follow new password policy 
  * requirements
    * \>= 12 characters
    * \>= 1 
      * uppercase letter
      * lowercase letter
      * number
      * special character

```bash
[auth.basic]
password_policy = true
```

## Disable login form

* == hide the Grafana login form

```bash
[auth]
disable_login_form = true
```

* uses  
  * authentication handled -- via -- external mechanisms OR SSO
