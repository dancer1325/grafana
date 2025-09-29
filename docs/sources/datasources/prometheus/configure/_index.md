---
aliases:
  - ../data-sources/prometheus/
  - ../features/datasources/prometheus/
description: Guide for configuring Prometheus in Grafana
keywords:
  - grafana
  - prometheus
  - guide
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Configure the Prometheus data source
title: Configure the Prometheus data source
weight: 200
refs:
  intro-to-prometheus:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/fundamentals/intro-to-prometheus/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/fundamentals/intro-to-prometheus/
  exemplars:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/fundamentals/exemplars/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/fundamentals/exemplars/
  configure-data-links-value-variables:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-data-links/#value-variables
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-data-links/#value-variables
  alerting-alert-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/alert-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/alert-rules/
  add-a-data-source:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/#add-a-data-source
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/#add-a-data-source
  prom-query-editor:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/prometheus/query-editor
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/prometheus/query-editor
  default-manage-alerts-ui-toggle:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#default_manage_alerts_ui_toggle
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#default_manage_alerts_ui_toggle
  provision-grafana:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/provisioning/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/provisioning/
  manage-alerts-toggle:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#default_manage_alerts_ui_toggle
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#default_manage_alerts_ui_toggle
  manage-recording-rules-toggle:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#default_allow_recording_rules_target_alerts_ui_toggle
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#default_allow_recording_rules_target_alerts_ui_toggle
  private-data-source-connect:
    - pattern: /docs/grafana/
      destination: docs/grafana-cloud/connect-externally-hosted/private-data-source-connect/
    - pattern: /docs/grafana-cloud/
      destination: docs/grafana-cloud/connect-externally-hosted/private-data-source-connect/
  configure-pdc:
    - pattern: /docs/grafana/
      destination: /docs/grafana-cloud/connect-externally-hosted/private-data-source-connect/configure-pdc/#configure-grafana-private-data-source-connect-pdc
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/connect-externally-hosted/private-data-source-connect/configure-pdc/#configure-grafana-private-data-source-connect-pdc
  azure-active-directory:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/azure-monitor/#configure-azure-active-directory-ad-authentication
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/azure-monitor/#configure-azure-active-directory-ad-authentication
  configure-grafana-configuration-file-location:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#configuration-file-location
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/setup-grafana/configure-grafana/#configuration-file-location
  grafana-managed-recording-rules:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/alerting-rules/create-recording-rules/create-grafana-managed-recording-rules/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/alerting-rules/create-recording-rules/create-grafana-managed-recording-rules/
---

# Configure the Prometheus data source

* goal
  * configure the Prometheus data source
  * AVAILABLE configuration options

## Before you begin

* requirements
  * `Organization administrator` role

* know
  * Prometheus-compatible database / you are using
  * Prometheus security configuration & security certificates & client keys

## Configure the data source using the UI

* **Connections** > **Add new connection** > **Prometheus**

## Configuration options

- **Name** 
  - == data source name
  - uses
    - | panels & queries
- **Default**
  - if on -> default data source |
    - dashboard panels
    - Explore
- **Connection:**
  - **Prometheus server URL**
    - if Prometheus is
      - running locally -> use http://localhost:9090
      - hosted | networked server -> server’s URL + port | Prometheus runs
        - _Example:_ http://prometheus.example.orgname:9090
      - running | container -> use http://host.docker.internal:9090
        - uses
          - Prometheus & Grafana run | DIFFERENT containers
- **Authentication:**
  - options
    - **Basic authentication**
      - MOST COMMON one
        - **User** 
        - **Password**
    - **Forward OAuth identity** 
      - forward the OAuth access token & OIDC ID token
    - **No authentication**
      - == access to the data source WITHOUT authentication
    - **TLS settings:**
      - [secure Prometheus API & UI Endpoints](https://prometheus.io/docs/guides/tls-encryption/)
      - **Add self-signed certificate**
        - == authenticate -- with a -- CA certificate
          - add **CA certificate**
      - **TLS client authentication**
        - **Server name**
          - == server name / verify the hostname | returned certificate
        - **Client certificate** 
          - generated -- from a -- Certificate Authority
        - **Client key** 
          - can ALSO be generated -- from a -- Certificate Authority (CA) or be self-signed
          - encrypts data BETWEEN the client -- & -- server
      - **Skip TLS verify** 
        - ❌NOT recommended❌
- **HTTP headers:**
  - **Header** 
    - == custom headerS
  - **Value** 
    - == header's value 
- **Advanced settings:**
  - **Advanced HTTP settings:**
    - **Allowed cookies**
      - == cookies / should be forwarded -- to the -- data source
      - by default,
        - Grafana proxy deletes ALL 
    - **Timeout** 
      - == HTTP request timeout (seconds)
- **Alerting:**
  - **Manage alerts via Alerting UI**
    - by default,
      - toggled on 
    - enables [data source-managed rules | Grafana Alerting](ref:alerting-alert-rules) / this data source
    - | 
      - `Mimir`,
        - it enables managing data source-managed rules and alerts
      - `Prometheus`,
        - it only supports viewing existing rules and alerts, which are displayed as data source-managed
    - Change this by setting the [`default_manage_alerts_ui_toggle`](ref:manage-alerts-toggle) option in the `grafana.ini` configuration file.
  - **Allow as recording rules target** 
    - Toggled on by default
    - This allows the data source to be selected as a target destination for writing [Grafana-managed recording rules](ref:grafana-managed-recording-rules)
    - When enabled, this data source will appear in the target data source list when creating or importing recording rules
    - When disabled, the data source will be filtered out from recording rules target selection
    - Change this by setting the [`default_allow_recording_rules_target_alerts_ui_toggle`](ref:manage-recording-rules-toggle) option in the `grafana.ini` configuration file.

**Interval behavior:**

- **Scrape interval** - Sets the standard scrape and evaluation interval in Prometheus. The default is `15s`. This interval determines how often Prometheus scrapes targets. Set it to match the typical scrape and evaluation interval in your Prometheus configuration file. If you set a higher value than your Prometheus configuration, Grafana will evaluate data at this interval, resulting in fewer data points.
- **Query timeout** - Sets the Prometheus query timeout. The default is `60s`. Without a timeout, complex or inefficient queries can run indefinitely, consuming CPU and memory resources.

**Query editor:**

- **Default editor** - Sets the default query editor. Options are `Builder` or `Code`. `Builder` mode helps you build queries using a visual interface. `Code` mode is geared for the experienced Prometheus user with prior expertise in PromQL. For more details on editor types refer to [Prometheus query editor](ref:prom-query-editor). You can switch easily code editors in the Query editor UI.
- **Disable metrics lookup** - Toggle on to disable the metrics chooser and metric and label support in the query field's autocomplete. This can improve performance for large Prometheus instances.

**Performance:**

- **Prometheus type** - Select the type of your Prometheus-compatible database, such as Prometheus, Cortex, Mimir, or Thanos. Changing this setting will save your current configuration. Different database types support different APIs. For example, some allow `regex` matching for label queries to improve performance, while others provide a metadata API. Setting this incorrectly may cause unexpected behavior when querying metrics and labels. Refer to your Prometheus documentation to ensure you select the correct type.
- **Cache level** - Sets the browser caching level for editor queries. There are four options: `Low`, `Medium`, `High`, or `None`. Higher cache settings are recommended for high cardinality data sources.
- **Incremental querying (beta)** - Toggle on to enable incremental querying. Enabling this feature changes the default behavior of relative queries. Instead of always requesting fresh data from the Prometheus instance, Grafana will cache query results and only fetch new records. This helps reduce database and network load.
  - **Query overlap window** - If you are using incremental querying, specify a duration (e.g., 10m, 120s, or 0s). The default is `10m`. This is a buffer of time added to incremental queries and this value is added to the duration of each incremental request.
- **Disable recording rules (beta)** - Toggle on to disable the recording rules. When recording rules are disabled, Grafana won't fetch and parse recording rules from Prometheus, improving dashboard performance by reducing processing overhead..

**Other settings:**

- **Custom query parameters** - Add custom parameters to the Prometheus query URL, which allow for more control over how queries are executed. Examples: `timeout`, `partial_response`, `dedup`, or `max_source_resolution`. Multiple parameters should be joined using `&`.
- **HTTP method** - Select either the `POST` or `GET` HTTP method to query your data source. `POST`is recommended and selected by default, as it supports larger queries. Select `GET` if you're using Prometheus version 2.1 or older, or if your network restricts `POST` requests.
  Toggle on
- **Series limit** - Number of maximum returned series. The limit applies to all resources (metrics, labels, and values) for both endpoints (series and labels). Leave the field empty to use the default limit (40000). Set to 0 to disable the limit and fetch everything — this may cause performance issues. Default limit is 40000.
- **Use series endpoint** - Enabling this option makes Grafana use the series endpoint (/api/v1/series) with the match[] parameter instead of the label values endpoint (/api/v1/label/<label_name>/values). While the label values endpoint is generally more performant, some users may prefer the series endpoint because it supports the `POST` method, whereas the label values endpoint only allows `GET` requests.

**Exemplars:**

Support for exemplars is available only for the Prometheus data source. For more information on exemplars refer to [Introduction to exemplars](ref:exemplars). An exemplar is a trace that represents a specific measurement taken within a given time interval.

Click the **+ sign** to add exemplars.

- **Internal link** - Toggle on to enable an internal link. This will display the data source selector, where you can choose the backend tracing data store for your exemplar data.
- **URL** - _(Visible if you **disable** `Internal link`)_ Defines the external link's URL trace backend. You can interpolate the value from the field by using the [`${__value.raw}` macro](ref:configure-data-links-value-variables).
- **Data source** - _(Visible when`Internal link` is enabled.)_ Select the data source that the exemplar will link to from the drop-down.
- **URL label** - Adds a custom display label to override the value of the `Label name` field.
- **Label name** - The name of the field in the `labels` object used to obtain the traceID property.
- **Remove exemplar link** - Click the **X** to remove existing links.

You can add multiple exemplars.

- **Private data source connect** - _Only for Grafana Cloud users._ Private data source connect, or PDC, allows you to establish a private, secured connection between a Grafana Cloud instance, or stack, and data sources secured within a private network. Click the drop-down to locate the URL for PDC. For more information regarding Grafana PDC refer to [Private data source connect (PDC)](ref:private-data-source-connect) and [Configure Grafana private data source connect (PDC)](https://grafana.com/docs/grafana-cloud/connect-externally-hosted/private-data-source-connect/configure-pdc/#configure-grafana-private-data-source-connect-pdc) for steps on setting up a PDC connection.

  If you use PDC with SIGv4 (AWS Signature Version 4 Authentication), the PDC agent must allow internet egress to`sts.<region>.amazonaws.com:443`.

  Click **Manage private data source connect** to open your PDC connection page and view your configuration details.

After you have configured your Prometheus data source options, click **Save & test** at the bottom to test out your data source connection.

You should see a confirmation dialog box that says:

**Successfully queried the Prometheus API.**

**Next, you can start to visualize data by building a dashboard, or by querying data in the Explore view.**

You can also remove a connection by clicking **Delete**.

## Provision the Prometheus data source

You can define and configure the data source in YAML files as part of the Grafana provisioning system. For more information about provisioning, and for available configuration options, refer to [Provision Grafana](ref:provision-grafana).

{{< admonition type="note" >}}
After you have provisioned a data source you cannot edit it.
{{< /admonition >}}

## Azure authentication settings

The Prometheus data source works with Azure authentication. To configure Azure authentication refer to [Configure Azure Active Directory (AD) authentication](ref:azure-active-directory).

In Grafana Enterprise, you need to update the .ini configuration file. Refer to [Configuration file location](ref:configure-grafana-configuration-file-location) to locate your .ini file.

Add the following setting in the **[auth]** section of the .ini configuration file:

```bash
[auth]
azure_auth_enabled = true
```

{{< admonition type="note" >}}
If you are using Azure authentication, don't enable `Forward OAuth identity`. Both methods use the same HTTP authorization headers, and the OAuth token will override your Azure credentials.
{{< /admonition >}}

## Recording rules (beta)

You can configure the Prometheus data source to disable recording rules in the data source configuration or provisioning file under `disableRecordingRules` in jsonData.

## Troubleshooting configuration issues

Refer to the following troubleshooting information as needed.

**Data doesn't appear in Metrics Drilldown:**

If you have successfully tested the connection to a Prometheus data source or are sending metrics to Grafana Cloud and there is no metric data appearing in Explore, make sure you've selected the correct data source from the data source drop-down menu. When using `remote_write` to send metrics to Grafana Cloud, the data source name follows the convention `grafanacloud-stackname-prom`.
