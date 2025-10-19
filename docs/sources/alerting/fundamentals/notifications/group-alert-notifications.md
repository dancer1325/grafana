---
canonical: https://grafana.com/docs/grafana/latest/alerting/fundamentals/notifications/group-alert-notifications/
description: Learn about how notification policies group alert notifications
keywords:
  - grafana
  - alerting
  - notification policies
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Group alert notifications
menuTitle: Grouping
weight: 114
refs:
  alert-labels:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/annotation-label/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/annotation-label/
  notification-policies:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/notification-policies/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/notification-policies/
  silences:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/create-silence/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/create-silence/
---

# Group alert notifications

* [tutorial](https://grafana.com/tutorials/alerting-get-started-pt3/)

## Group notifications

* == notification policy's configuration
  * 💡-- via -- `Group by`💡
    * by default, by alert rule -- `alertname` & `grafana_folder` labels --

![](/grafana/media/docs/alerting/alerting-notification-policy-diagram-with-labels-v3.png)

### Group by alert rule or labels

### 1! group / ALL alerts

* | Default policy,
  * set `Group by` = "" 

### Disable grouping ==separate notification / EACH alert

* set `Group by` = "..." 

## Timing options

* == notification policy's configuration
* == how often to send the notification / EACH [group of alerts](#group-notifications)
  * == delaying the delivery of notifications
* allows
  * grouping incoming alerts | 1! notification
* == 
  - **[Group wait](#group-wait)**
    - time to wait BEFORE sending the FIRST notification -- for a -- NEW group of alerts
  - **[Group interval](#group-interval)**
    - time to wait BEFORE sending a notification about changes | alert group
  - **[Repeat interval](#repeat-interval)**
    - if the group has NOT changed since last notification -> time to wait BEFORE sending a notification 

![](/grafana/media/docs/alerting/alerting-timing-options-flowchart-v2.png)

<!--
flowchart LR
    A((First alert)) -///-> B
    B[Group wait <br/>  notification] -///-> C
    B -- no changes -///-> D
    C[Group interval <br/>  notification] -- no changes -///-> D
    C -- group changes -///-> C
    D[Repeat interval <br/>  notification]
-->

### Group wait

**Default**: 30 seconds

Group wait is the duration Grafana waits before sending the first notification for a new group of alerts.

This option helps reduce the number of notifications sent for related alerts occurring within a short time frame
* The longer the group wait, the more time other alerts have to be included in the initial notification of the new group
* The shorter the group wait, the earlier the first notification is sent, but at the risk of not including some alerts.

If an alert is resolved before the duration elapses, no notification is sent for that alert
* This reduces noise from flapping alerts.

**Example**

Consider a notification policy that:

- Matches all alert instances with the `team` label—matching labels equals to `team=~.+`.
- Groups notifications by the `team` label—one group for each distinct `team`.
- Sets the Group wait timer to `30s`.

| Time               | Incoming alert instance        | Notification policy group | Number of instances |                                                                         |
| ------------------ | ------------------------------ | ------------------------- | ------------------- | ----------------------------------------------------------------------- |
| 00:00              | `alertname=f1` `team=frontend` | `frontend`                | 1                   | Starts the group wait timer of the `frontend` group.                    |
| 00:10              | `alertname=f2` `team=frontend` | `frontend`                | 2                   |                                                                         |
| 00:20              | `alertname=b1` `team=backend`  | `backend`                 | 1                   | Starts the group wait timer of the `backend` group.                     |
| 00:30<sup>\*</sup> |                                | `frontend`                | 2                   | Group wait elapsed. <br/> Send initial notification reporting 2 alerts. |
| 00:35              | `alertname=b2` `team=backend`  | `backend`                 | 2                   |                                                                         |
| 00:40              | `alertname=b3` `team=backend`  | `backend`                 | 3                   |                                                                         |
| 00:50<sup>\*</sup> |                                | `backend`                 | 3                   | Group wait elapsed. <br/> Send initial notification reporting 3 alerts. |

### Group interval

**Default**: 5 minutes

If an alert was too late to be included in the first notification due to group wait, it is included in subsequent notifications after group interval.

Group interval is the duration to wait before sending notifications about group changes. A group change occurs when:

- A new firing alert is added to the group.
- An existing alert is resolved.

**Example**

Here are the related excerpts from the previous example:

| Time               | Incoming alert instance | Notification policy group | Number of instances |                                                                                                         |
| ------------------ | ----------------------- | ------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------- |
| 00:30<sup>\*</sup> |                         | `frontend`                | 2                   | Group wait elapsed and starts Group interval timer. <br/> Send initial notification reporting 2 alerts. |
| 00:50<sup>\*</sup> |                         | `backend`                 | 3                   | Group wait elapsed and starts Group interval timer. <br/> Send initial notification reporting 3 alerts. |

And below is the continuation of the example setting the Group interval timer to 5 minutes:

| Time               | Incoming alert instance        | Notification policy group | Number of instances |                                                                                                |
| ------------------ | ------------------------------ | ------------------------- | ------------------- | ---------------------------------------------------------------------------------------------- |
| 01:30              | `alertname=f3` `team=frontend` | `frontend`                | 3                   |                                                                                                |
| 02:30              | `alertname=f4` `team=frontend` | `frontend`                | 4                   |                                                                                                |
| 05:30<sup>\*</sup> |                                | `frontend`                | 4                   | Group interval elapsed and resets timer. <br/> Send one notification reporting 4 alerts.       |
| 05:50<sup>\*</sup> |                                | `backend`                 | 3                   | Group interval elapsed and resets timer. <br/> No group changes, and do not send notification. |
| 08:00              | `alertname=f4` `team=backend`  | `backend`                 | 4                   |                                                                                                |
| 10:30<sup>\*</sup> |                                | `frontend`                | 4                   | Group interval elapsed and resets timer. <br/> No group changes, and do not send notification. |
| 10:50<sup>\*</sup> |                                | `backend`                 | 4                   | Group interval elapsed and resets timer. <br/> Send one notification reporting 4 alerts.       |

**How it works**

Once the first notification has been sent for a new group of alerts, the group interval timer starts.

When the group interval timer elapses, the system resets the group interval timer and sends a notification only if there were group changes. This process repeats until there are no more alerts.

It's important to note that an alert instance exits the group after being resolved and notified of its state change. When no alerts remain, the group is deleted, and then the group wait timer handles the first notification for the next incoming alert once again.

### Repeat interval

**Default**: 4 hours

Repeat interval acts as a reminder that alerts in the group are still firing.

The repeat interval timer decides how often notifications are sent (or repeated) if the group has not changed since the last notification.

**How it works**

Repeat interval is evaluated every time the group interval resets. If the alert group has not changed and the time since the last notification was longer than the repeat interval, then a notification is sent as a reminder that the alerts are still firing.

Repeat interval must not only be greater than or equal to group interval, but also must be a multiple of Group interval. If Repeat interval is not a multiple of group interval it is coerced into one. For example, if your Group interval is 5 minutes, and your Repeat interval is 9 minutes, the Repeat interval is rounded up to the nearest multiple of 5 which is 10 minutes.

The maximum duration of the repeat interval is 5 days, constrained by the default value of the `notification_log_retention` setting in Grafana.

**Example**

Here are the related excerpts from the previous example:

| Time               | Incoming alert instance | Notification policy group | Number of instances |                                                          |
| ------------------ | ----------------------- | ------------------------- | ------------------- | -------------------------------------------------------- |
| 05:30<sup>\*</sup> |                         | `frontend`                | 4                   | Group interval resets. <br/> Send the last notification. |
| 10:50<sup>\*</sup> |                         | `backend`                 | 4                   | Group interval resets. <br/> Send the last notification. |

And below is the continuation of the example setting the Repeat interval timer to 4 hours:

| Time     | Incoming alert instance | Notification policy group | Number of instances |                                                                                                                                                             |
| -------- | ----------------------- | ------------------------- | ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 04:05:30 |                         | `frontend`                | 4                   | Group interval resets. The time since the last notification was no longer than the repeat interval.                                                         |
| 04:10:30 |                         | `frontend`                | 4                   | Group interval resets. The time since the last notification was longer than the repeat interval. <br/> Send one notification reminding the 4 firing alerts. |
| 04:10:50 |                         | `backend`                 | 4                   | Group interval resets. The time since the last notification was no longer than the repeat interval.                                                         |
| 04:15:50 |                         | `backend`                 | 4                   | Group interval resets. The time since the last notification was longer than the repeat interval. <br/> Send one notification reminding the 4 firing alerts. |
