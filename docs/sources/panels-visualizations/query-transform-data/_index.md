---
aliases:
  - ../panels/expressions/
  - ../panels/inspect-panel/
  - ../panels/queries/
  - ../panels/query-a-data-source/
  - ../panels/query-a-data-source/about-queries/
  - ../panels/query-a-data-source/add-a-query/
  - ../panels/query-a-data-source/manage-queries/
  - ../panels/query-a-data-source/navigate-query-tab/
  - ../panels/query-options/
  - ../panels/reference-query-options/
  - ../panels/share-query-results/
  - manage-queries/
  - query-options/
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Query and transform data
description: Query and transform your data
weight: 40
refs:
  data-sources:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/connect-externally-hosted/data-sources/
  built-in-core-data-sources:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/#built-in-core-data-sources
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/connect-externally-hosted/data-sources/#built-in-core-data-sources
  use-expressions-to-manipulate-data:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/expression-queries/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/expression-queries/
  global-variables:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/variables/add-template-variables/#global-variables
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/dashboards/variables/add-template-variables/#global-variables
  plugin-management:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/plugin-management/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/plugin-management/
  recorded-queries:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/recorded-queries/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/administration/recorded-queries/
  special-data-sources:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/#special-data-sources
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/connect-externally-hosted/data-sources/#special-data-sources
---

# Query and transform data

* see [Grafana data sources](ref:data-sources)

* data source
  * **queries**
    * return data / Grafana can
      * **transform**
      * visualize
  * OWN query language / EACH data source

## About queries

* query
  * := question | query language -- used by the -- data source
    * see [Data sources](ref:data-sources)
  * configuration
    * | panel's data source options
      * query frequency
      * data collection limits
  * <= 26 queries / panel

### Query editors

* specific query editor features / data source 
  - for Grafana built-in data sources -> see [Built-in core data sources](ref:built-in-core-data-sources)
  - for data sources / -- installed as -- plugins -> see
    - Data source plugins | Grafana's -> [plugin catalog](/grafana/plugins/)
    - Grafana Enterprise data source plugin -> [Enterprise plugins index](/docs/plugins/).

### Query syntax

* ⚠️DIFFERENT query language / data source ⚠️
  * _Example1:_ PostgreSQL

    ```
    SELECT hostname FROM host WHERE region IN($region)
    ```

  * _Example2:_ PromQL

    ```
    query_result(max_over_time(<metric>[${__range_s}s]) != <state>)
    ```

### Saved queries

* requirements
  * Grafana Enterprise & Grafana Cloud

* current status
  * [public preview](https://grafana.com/docs/release-life-cycle/)

* allows
  * being reused -- by -- you & OTHERS | your organization

* uses
  * reuse queries

* **Saved queries** drawer
  * * Explore > Add from saved queries
  * enable filter by
    * if you filter by MULTIPLE
      * datasource -> `OR` operator
      * user name -> `OR` operator
      * tag -> `AND` operator
  * duplicate, lock, unlock saved queries

![](/grafana/media/docs/panels-visualizations/SavedQuery.png)

#### Save a query

To save a query you've created:

1. From the query editor, click the **Save query** icon:

   {{< figure src="/media/docs/grafana/panels-visualizations/screenshot-save-query-v12.2.png" max-width="750px" alt="Save a query" >}}

1. In the **Saved queries** drawer, enter a title for the query that will make it easy to find later.
1. (Optional) Enter a description and relevant tags.
1. Clear the **Share query with all users** checkbox if you only want the saved query to be available to you.
1. Click **Save**.

#### Known limitations

- No validation is performed when you save a query, so it's possible to save an invalid query. You should confirm the query is working properly before you save it.
- Saved queries are currently accessible from the query editors in Dashboards and Explore.
- You can save a maximum of 1000 queries.
- Users with the Viewer role who have access to Explore can use saved queries, but can't write them.
- If you have multiple queries open in Explore and you edit one of them by way of the **Edit in Explore** function in the **Saved queries** drawer, the edited query replaces your open queries in Explore.

## Navigate the Query tab

* panel's Query tab -- consists of --
  - **Data source selector:**
    - == data source -- to -- query
  - **Query options:**
    - sets
      - MAXIMUM data retrieval parameters
      - query execution time intervals
      - ...
  - **Query inspector button:**
    - Opens the query inspector panel
    - uses
      - check -- to optimize -- your query
  - **Query editor list:**
  - **Expressions:**
    - see [here](expression-queries)

## Add a query

1. Dashboard > choose 1 > choose 1 panel's Edit (== go to panel editor)
1. | Data section > **Queries** tab
   1. select a **Data source**
   1. configure [Query options](#query-options)
1. ways to add a query
   - **Add query** by yourself
   - **Add from saved queries**
   - **Replace EXISTING query -- with -- saved query**
1. [Save query](#saved-queries)
   2. OPTIONAL

![](/grafana/media/docs/panels-visualizations/queryTransformAddQuery.png)

## Manage queries

Grafana organizes queries in collapsible query rows.
Each query row contains a query editor and is identified with a letter (A, B, C, and so on).

You can:

<!-- prettier-ignore-start -->
| Icon    | Description                                  |
| ------- | -------------------------------------------- |
| {{< figure src="/static/img/docs/queries/query-editor-help-7-4.png" max-width="30px" max-height="30px" alt="Help icon" >}} | Toggles query editor help. If supported by the data source, click this icon to display information on how to use the query editor or provide quick access to common queries. |
| {{< figure src="/media/docs/grafana/panels-visualizations/create-recorded-query-icon.png" max-width="30px" max-height="30px" alt="Create recorded query icon" >}} | Create [recorded queries](ref:recorded-queries) so you can see trends over time by taking a snapshot of a data point on a set interval (Enterprise and Cloud only). |
| {{< figure src="/media/docs/grafana/panels-visualizations/save-to-query-icon.png" max-width="30px" max-height="30px" alt="Save query icon" >}} | Save query. Saves the query so it can be reused. Access saved queries by clicking **+ Add saved query**. For more information, refer to [Saved queries](#saved-queries) (Enterprise and Cloud only). |
| {{< figure src="/static/img/docs/queries/duplicate-query-icon-7-0.png" max-width="30px" max-height="30px" alt="Duplicate icon" >}} | Copies a query. Duplicating queries is useful when working with multiple complex queries that are similar and you want to either experiment with different variants or do minor alterations. |
| {{< figure src="/static/img/docs/queries/hide-query-icon-7-0.png" max-width="30px" max-height="30px" alt="Hide icon" >}} | Hides a query. Grafana does not send hidden queries to the data source. |
| {{< figure src="/static/img/docs/queries/remove-query-icon-7-0.png" max-width="30px" max-height="30px" alt="Remove icon">}} | Removes a query. Removing a query permanently deletes it, but sometimes you can recover deleted queries by reverting to previously saved versions of the panel. |
| {{< figure src="/static/img/docs/queries/query-drag-icon-7-2.png" max-width="30px" max-height="30px" alt="Drag icon" >}} | Reorders queries. Change the order of queries by clicking and holding the drag icon, then drag queries where desired. The order of results reflects the order of the queries, so you can often adjust your visual results based on query order. |
<!-- prettier-ignore-end -->

## Query options

Click **Query options** next to the data source selector to see settings for the selected data source.
Changes you make here affect only queries made in this panel.

{{< figure src="/media/docs/grafana/panels-visualizations/screenshot-query-options-v11.6.png" max-width="750px" alt="Data source query options" >}}

Grafana sets defaults that are shown in dark gray text.
Changes are displayed in white text.
To return a field to the default setting, delete the white text from the field.

Panel data source query options include:

- **Max data points** - If the data source supports it, this sets the maximum number of data points for each series returned.
  If the query returns more data points than the max data points setting, then the data source reduces the number of points returned by aggregating them together by average, max, or another function.

  You can limit the number of points to improve query performance or smooth the visualized line.
  The default value is the width (or number of pixels) of the graph, because you can only visualize as many data points as the graph panel has room to display.

  With streaming data, Grafana uses the max data points value for the rolling buffer.
  Streaming is a continuous flow of data, and buffering divides the stream into chunks.
  For example, Loki streams data in its live tailing mode.

- **Min interval** - Sets a minimum limit for the automatically calculated interval, which is typically the minimum scrape interval.
  If a data point is saved every 15 seconds, you don't benefit from having an interval lower than that.
  You can also set this to a higher minimum than the scrape interval to retrieve queries that are more coarse-grained and well-functioning.

  {{< admonition type="note" >}}
  The **Min interval** corresponds to the min step in Prometheus. Changing the Prometheus interval can change the start and end of the query range because Prometheus aligns the range to the interval. Refer to [Min step](https://grafana.com/docs/grafana/latest/datasources/prometheus/query-editor/#min-step) for more details.
  {{< /admonition >}}

- **Interval** - Sets a time span that you can use when aggregating or grouping data points by time.

  Grafana automatically calculates an appropriate interval that you can use as a variable in templated queries.
  The variable is measured in either seconds (`$__interval`) or milliseconds (`$__interval_ms`).

  Intervals are typically used in aggregation functions like sum or average.
  For example, this is a Prometheus query that uses the interval variable: `rate(http_requests_total[$__interval])`.

  This automatic interval is calculated based on the width of the graph.
  As the user zooms out on a visualization, the interval grows, resulting in a more coarse-grained aggregation.
  Likewise, if the user zooms in, the interval decreases, resulting in a more fine-grained aggregation.

  For more information, refer to [Global variables](ref:global-variables).

- **Relative time** - Overrides the relative time range for individual panels, which causes them to be different than what is selected in the dashboard time picker in the top-right corner of the dashboard.
  You can use this to show metrics from different time periods or days on the same dashboard.

  {{< admonition type="note">}}
  Panel time overrides have no effect when the dashboard's time range is absolute.
  {{< /admonition >}}

  | Example          | Relative time field |
  | ---------------- | ------------------- |
  | Last 5 minutes   | `now-5m`            |
  | The day so far   | `now/d`             |
  | Last 5 days      | `now-5d/d`          |
  | This week so far | `now/w`             |
  | Last 2 years     | `now-2y/y`          |

{{< docs/play title="Time range override" url="https://play.grafana.org/d/000000041/" >}}

- **Time shift** - Overrides the time range for individual panels by shifting its start and end relative to the time picker.
  For example, you can shift the time range for the panel to be two hours earlier than the dashboard time picker.

  {{< admonition type="note">}}
  Panel time overrides have no effect when the dashboard's time range is absolute.
  {{< /admonition >}}

  | Example              | Time shift field |
  | -------------------- | ---------------- |
  | Last entire week     | `1w/w`           |
  | Two entire weeks ago | `2w/w`           |
  | Last entire month    | `1M/M`           |
  | This entire year     | `1d/y`           |
  | Last entire year     | `1y/y`           |

- **Cache timeout** - _(Visible only if available in the data source)_ Overrides the default cache timeout if your time series store has a query cache.
  Specify this value as a numeric value in seconds.
