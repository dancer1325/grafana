---
aliases:
  - ../silences/create-silence/ # /docs/grafana/<GRAFANA_VERSION>/alerting/silences/create-silence/
  - ../silences/edit-silence/ # /docs/grafana/<GRAFANA_VERSION>/alerting/silences/edit-silence/
  - ../silences/linking-to-silence-form/ # /docs/grafana/<GRAFANA_VERSION>/alerting/silences/linking-to-silence-form/
  - ../silences/remove-silence/ # /docs/grafana/<GRAFANA_VERSION>/alerting/silences/remove-silence/
  - ../unified-alerting/silences/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/silences/
  - ../silences/ # /docs/grafana/<GRAFANA_VERSION>/alerting/silences/
  - ../manage-notifications/create-silence/ # /docs/grafana/<GRAFANA_VERSION>/alerting/manage-notifications/create-silence/
canonical: https://grafana.com/docs/grafana/latest/alerting/configure-notifications/create-silence/
description: Create silences to stop notifications from getting created for a specified window of time
keywords:
  - grafana
  - alerting
  - silence
  - mute
  - active
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Configure silences
weight: 440
refs:
  configure-alertmanager:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/set-up/configure-alertmanager/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/set-up/configure-alertmanager/
  silence-url:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/template-notifications/reference/#alert
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/template-notifications/reference/#alert
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
  shared-mute-timings:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/mute-timings/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/mute-timings/
  alertmanager-architecture:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/set-up/configure-alertmanager/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/set-up/configure-alertmanager/
---

# Configure silences

* Silences 
  * == 💡mute alerts | given time💡
    * ALTHOUGH, ❌NOT interrupt alert evaluation❌
    * -- based on -- labels
  * uses
    * prevent alert notifications
      * _Examples:_ incident response OR maintenance window
  * are assigned -- to a -- [⚠️specific⚠️ Alertmanager](ref:alertmanager-architecture)
    * == ONLY suppress notifications / that Alertmanager

## Mute and active timings vs silences

* [here](/grafana/docs/sources/shared/alerts/mute-timings-vs-silences.md)

## Add silences

* label matchers
  * == **Label** + **Operator** + **Value**
  * if you use MULTIPLE -> combined -- via -- AND logical operator
  * allows
    * linking alert rules -- to -- [notification policies](ref:shared-notification-policies) & [silences](ref:shared-silences)

  | Operator | Description                                        |
  | -------- | -------------------------------------------------- |
  | `=`      | Select labels that are exactly equal to the value. |
  | `!=`     | Select labels that are not equal to the value.     |
  | `=~`     | Select labels that regex-match the value.          |
  | `!~`     | Select labels that do not regex-match the value.   |

  * [here](/grafana/docs/sources/shared/alerts/how_label_matching_works.md)

## Rule-specific silences

Rule-specific silences are silences that apply only to a specific alert rule
* They're created when you silence an alert rule directly using the **Silence notifications** action in the UI.

As opposed to general silences, rule-specific silence access is tied directly to the alert rule they act on
* They can be created manually by including the specific label matcher: `__alert_rule_uid__=<alert rule UID>`.

## URL link to a silence form

Default notification messages often include a link to silence alerts.

In custom notification templates, you can use [`.Alert.SilenceURL`](ref:silence-url) to redirect users to the UI where they can silence the given alert.

If [`.Alert.SilenceURL`](ref:silence-url) doesn’t fit your specific use case, you can also create a custom silence link for your custom templates.

{{< collapse title="Create a custom silence link" >}}

When linking to a silence form, provide the default matching labels and comment via `matcher` and `comment` query parameters
* The `matcher` parameter should be in the following format `[label][operator][value]` where the `operator` parameter can be one of the following: `=` (equals, not regular expression), `!=` (not equals, not regular expression), `=~` (equals, regular expression), `!~` (not equals, regular expression).
The URL can contain many query parameters with the key `matcher`.
For example, to link to silence form with matching labels `severity=critical` & `cluster!~europe-.*` and comment `Silence critical EU alerts`, create a URL `https://mygrafana/alerting/silence/new?matcher=severity%3Dcritical&matcher=cluster!~europe-*&comment=Silence%20critical%20EU%20alert`.

To link to a new silence page for an external Alertmanager, add a `alertmanager` query parameter with the Alertmanager data source name.

{{< /collapse >}}

## Inhibition rules

* supported | Prometheus Alertmanager
  * [how to configure a Prometheus Alertmanager](ref:configure-alertmanager)

* ❌NOT supported | Grafana Alertmanager❌
  * [feature request](https://github.com/grafana/grafana/issues/68822)
