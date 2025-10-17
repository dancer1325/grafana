---
aliases:
  - ../../configure-alertmanager/ # /docs/grafana/<GRAFANA_VERSION>/configure-alertmanager/
  - ../unified-alerting/fundamentals/alertmanager/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/fundamentals/alertmanager/
  - ../manage-notifications/alertmanager/ # /docs/grafana/<GRAFANA_VERSION>/alerting/manage-notifications/alertmanager/
  - ../fundamentals/alertmanager/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alertmanager/
  - ../fundamentals/notifications/alertmanager/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/alertmanager
canonical: https://grafana.com/docs/grafana/latest/alerting/set-up/configure-alertmanager/
description: Learn about Alertmanagers and set up Alerting to use other Alertmanagers
keywords:
  - grafana
  - alerting
  - set up
  - configure
  - external Alertmanager
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Configure Alertmanagers
weight: 200
refs:
  configure-grafana-alerts-notifications:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-grafana-managed-rule/#configure-notifications
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-grafana-managed-rule/#configure-notifications
  configure-notification-policies:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/create-notification-policy/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/create-notification-policy/
  alertmanager-contact-point:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/configure-notifications/manage-contact-points/integrations/configure-alertmanager/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/configure-notifications/manage-contact-points/integrations/configure-alertmanager/
  alertmanager-data-source:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/alertmanager/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/connect-externally-hosted/data-sources/alertmanager/
  notifications:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/notifications/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/notifications/
---


# Configure Alertmanagers

* Grafana Alerting's architecture
  * 👀-- based on the -- Prometheus alerting system's architecture👀
  * == Grafana sends firing and resolved alerts -- to an -- Alertmanager / [handle notifications](ref:notifications)
    * == 👀alert rule evaluation is decoupled -- from -- notification handling👀
      * -> BETTER scalability

    ![](/grafana/media/docs/alerting/alerting-alertmanager-architecture.png)

  * 👀built-in **Grafana Alertmanager**👀

## Alertmanager resources

* managed / EACH Alertmanager
* they are
  - Contact points and notification templates
  - Notification policies and mute timings
  - Silences
  - Active notifications

* `Choose Alertmanager` dropdown
  * allows
    * switch BETWEEN Alertmanagers

![](/grafana/media/docs/alerting/alerting-choose-alertmanager.png)

## Types of Alertmanagers | Grafana

- **Grafana Alertmanager**
  - == built-in Alertmanager / extends the [Prometheus Alertmanager](https://prometheus.io/docs/alerting/latest/alertmanager/)
  - allows
    - ⚠️ONLY handle Grafana-managed alerts⚠️

- **Cloud Alertmanager**
  - Each Grafana Cloud instance comes preconfigured with an additional Alertmanager (`grafanacloud-STACK_NAME-ngalertmanager`) from the Mimir (Prometheus) instance running in the Grafana Cloud Stack.
  - The Cloud Alertmanager is available exclusively in Grafana Cloud and can handle both Grafana-managed and data source-managed alerts.

- **Other Alertmanagers**
  - Grafana Alerting also supports sending alerts to other Alertmanagers, such as the [Prometheus Alertmanager](https://prometheus.io/docs/alerting/latest/alertmanager/), which can handle both Grafana-managed and data source-managed alerts.

Grafana Alerting supports using a combination of Alertmanagers and can [enable other Alertmanagers to receive Grafana-managed alerts](#enable-an-alertmanager-to-receive-grafana-managed-alerts)
The decision often depends on your alerting setup and where your alerts are generated.

For example, if you already have an Alertmanager running in your on-premises or cloud infrastructure to handle Prometheus alerts,
you can forward Grafana-managed alerts to the same Alertmanager for unified notification handling.

## Add an Alertmanager

Alertmanagers should be configured as data sources using Grafana Configuration from the main Grafana navigation menu. To add an Alertmanager, complete the following steps.

{{< docs/shared lookup="alerts/add-alertmanager-ds.md" source="grafana" version="<GRAFANA_VERSION>" >}}

For provisioning instructions, refer to the [Alertmanager data source documentation](ref:alertmanager-data-source).

After adding an Alertmanager, you can use the Grafana Alerting UI to manage notification policies, contact points, silences, and other alerting resources from within Grafana.

{{< admonition type="note" >}}
When using Prometheus, you can manage silences in the Grafana Alerting UI. However, other Alertmanager resources such as contact points, notification policies, and templates are read-only because the Prometheus Alertmanager HTTP API does not support updates for these resources.
{{< /admonition >}}

When using multiple Alertmanagers, use the `Choose Alertmanager` dropdown to switch between Alertmanagers.

## Enable an Alertmanager to receive Grafana-managed alerts

After enabling **Receive Grafana Alerts** in the Data Source Settings, you must also configure the Alertmanager in the Alerting Settings page. Grafana supports enabling one or multiple Alertmanagers to receive all generated Grafana-managed alerts.

1. In the left-side menu, click **Alerts & IRM** and then **Alerting**.
1. Click **Settings** to view the list of configured Alertmanagers.
1. For the selected Alertmanager, click the **Enable/Disable** button to toggle receiving Grafana-managed alerts. When activated, the Alertmanager displays `Receiving Grafana-managed alerts`.

{{< figure src="/media/docs/alerting/grafana-alerting-settings.png" max-width="750px" alt="Grafana Alerting Settings page" >}}

All Grafana-managed alerts are forwarded to Alertmanagers marked as `Receiving Grafana-managed alerts`.

{{< admonition type="note" >}}
Grafana Alerting does not support forwarding Grafana-managed alerts to the AlertManager in Amazon Managed Service for Prometheus. For more details, refer to [this GitHub issue](https://github.com/grafana/grafana/issues/64064).
{{< /admonition >}}

## Use an Alertmanager as a contact point to receive specific alerts

The previous instructions enable sending **all** Grafana-managed alerts to an Alertmanager.

To send **specific** alerts to an Alertmanager, configure the Alertmanager as a contact point. You can then assign this contact point to notification policies or individual alert rules.

For detailed instructions, refer to:

- [Alertmanager contact point](ref:alertmanager-contact-point)
- [Configure Grafana-managed alert rules](ref:configure-grafana-alerts-notifications)
- [Configure notification policies](ref:configure-notification-policies)

## Manage Alertmanager configurations

On the Settings page, you can also manage your Alertmanager configurations.

- Manage version snapshots for the built-in Alertmanager, which allows administrators to roll back unintentional changes or mistakes in the Alertmanager configuration.
- Compare the historical snapshot with the latest configuration to see which changes were made.
