---
aliases:
  - ../notification-policies/notifications/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notification-policies/notifications/
canonical: https://grafana.com/docs/grafana/latest/alerting/fundamentals/notifications/notification-policies/
description: Learn about how notification policies work and are structured
keywords:
  - grafana
  - alerting
  - alertmanager
  - notification policies
  - contact points
  - silences
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Notification policies
weight: 113
refs:
  shared-alert-labels:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/annotation-label/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/annotation-label/
  shared-notification-policies:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/notification-policies/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/notification-policies/
  shared-silences:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/create-silence/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/create-silence/
  contact-points:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/contact-points/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/contact-points/
  notification-timings:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/group-alert-notifications/#timing-options
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/group-alert-notifications/#timing-options
  mute-timings:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/mute-timings/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/mute-timings/
  group-alert-notifications:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/group-alert-notifications/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/group-alert-notifications/
---

# Notification policies

* Notification policies
  * != list
  * == [tree structure](https://en.wikipedia.org/wiki/Tree_structure)
    - root
      - == **Default notification policy**
    - child policies
    - sibling policies
      - == SAME parent & hierarchical level
  * allows flexibly
    * how to 
      * handle notifications
      * minimize alert noise
    * [group MULTIPLE alert instances -- into a -- 1! notification](ref:group-alert-notifications) 

* alert instances
  * are routed -- , based on label matchers, to -- [notification policies](#routing)

  ![](/grafana/media/docs/alerting/how-alerting-works.png)

* Notification policy
  * == set of label matcherS (>=0) / 
    * specify the alerts | they are or NOT interested in handling

* matching policy
  * == notification policy / label matchers match the alert instance’s labels

* alert rules
  * can be linked -- , via [labels](ref:shared-alert-labels) & [label matchers](/grafana/docs/sources/shared/alerts/how_label_matching_works.md), to -- [notification policies](ref:shared-notification-policies) and [silences](ref:shared-silences)

![](/grafana/media/docs/alerting/notification-routing.png)

* [tutorial](https://grafana.com/tutorials/alerting-get-started-pt2/)

## Routing

* steps to identify the notification policies / handle an alert instance
  * FROM top of EXISTING notification policies /
    * start from the default notification policy
  * if a matching policy is found -> by default, NOT look for the sibling policies
    * if you want sibling policies handle the alert instance as well -> enable **Continue matching siblings**

{{< collapse title="Routing example" >}}

Here's a breakdown of the previous example:

**Pod stuck in CrashLoop** does not have a `severity` label, so none of its child policies are matched
* It does have a `team=operations` label, so the first policy is matched.

The `team=security` policy is not a match and **Continue matching siblings** was not configured for that policy.

**Disk Usage – 80%** has both a `team` and `severity` label, and matches a child policy of the operations team.

{{< admonition type="note" >}}
When an alert matches both a parent policy and a child policy (like it does in this case), the routing follows the child policy (`severity`) as it provides a more specific match.
{{< /admonition >}}

**Unauthorized log entry** has a `team` label but does not match the first policy (`team=operations`) since the values are not the same, so it will continue searching and match the `team=security` policy
* It does not have any child policies, so the additional `severity=high` label is ignored.

{{< /collapse >}}

This routing and tree structure makes it convenient to organize and handle alerts for dedicated teams, while also narrowing down specific cases within the team by applying additional labels.

## Inheritance

In addition to child policies being a useful concept for routing alert instances, they also inherit properties from their parent policy
* This also applies to child policies of the default notification policy.

By default, a child policy inherits the following notification properties from its parent:

- [Contact point](ref:contact-points)
- [Grouping options](ref:group-alert-notifications)
- [Timing options](ref:notification-timings)

Then, each policy can overwrite these properties if needed.

The inheritance of notification properties, together with the routing process, is an effective method for grouping related notifications and handling specific cases through child policies.

**Inheritance example**

{{< figure src="/media/docs/alerting/notification-inheritance.png" max-width="750px" alt="Simple example inhering notification settings" >}}

This example shows how the notification policy tree from the previous example allows the child policies of the `team=operations` to inherit its contact point
* In this way, you can avoid specifying the same contact point multiple times for each child policy.
