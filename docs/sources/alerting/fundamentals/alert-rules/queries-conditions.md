---
aliases:
  - ../../fundamentals/evaluate-grafana-alerts/ # /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/evaluate-grafana-alerts/
  - ../../unified-alerting/fundamentals/evaluate-grafana-alerts/ # /docs/grafana/<GRAFANA_VERSION>/alerting/unified-alerting/fundamentals/evaluate-grafana-alerts/
canonical: https://grafana.com/docs/grafana/latest/alerting/fundamentals/alert-rules/queries-conditions/
description: Define queries to get the data you want to measure and conditions that need to be met before an alert rule fires
keywords:
  - grafana
  - alerting
  - queries
  - conditions
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Queries and conditions
weight: 104
refs:
  dynamic-threshold-example:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/best-practices/dynamic-thresholds/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/best-practices/dynamic-thresholds/
  alert-instance:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/#alert-instances
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/#alert-instances
  state-and-health:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/fundamentals/state-and-health/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/fundamentals/state-and-health/
  query-transform-data:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/
  math-operation:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/expression-queries/#math
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/expression-queries/#math
  resample-operation:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/expression-queries/#resample
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/expression-queries/#resample
  reduce-operation:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/query-transform-data/expression-queries/#reduce
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/query-transform-data/expression-queries/#reduce
  table-data-example:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/alerting/best-practices/table-data/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/alerting-and-irm/alerting/best-practices/table-data/
---

# Queries and conditions

## Data source queries

* Alerting queries
  * == queries / done | Grafana panels
  * Grafana-managed alerts' restrictions
    * [data sources / `alerting` is enabled](/grafana/plugins/data-source-plugins/?features=alerting)
  * 's editor
    * customized user interface / data source
  * ⚠️ALLOWED data types⚠️ 
    1 **Time series data** 
      * query returns a >=1 time series / EACH series must be [reduced](#reduce) -- to a -- 1! numeric value 
        * Reason:🧠evaluate the alert condition🧠
        * 👀EACH time series is evaluated -- as a -- separate [alert instance](ref:alert-instance)👀 
    1. **Tabular data** 
      * query returns data | table format / 1! numeric column / EACH row
        * Reason:🧠evaluate the alert condition🧠
        * 👀EACH time series or table row is evaluated -- as a -- separate [alert instance](ref:alert-instance)👀
      * See a [tabular data example](ref:table-data-example)

## Alert condition

* alert condition
  * == query OR expression / determines whether the alert fires OR NOT
  * types
    * | use **Default options**,
      * `When query` 
        * [reduces the query data](#reduce)
    * | use **Advanced options**,
      * you can choose

## Advanced options: Expressions

* requirements
  * Grafana-managed alerts
  * enable the **Advanced options**

* allows
  * | retrieved data, performing
    * transformations 
    * calculations,
    * aggregations

### Reduce

* 👀range vector is converted -- into a -- 1! number👀
* 's input
  * \>=1 range vector time series
* 's return
  * EACH series are transformed -- into -- 1! number
    * Reason:🧠compare | alert condition🧠

* ALLOWED functions
  * `Min`,
  * `Max`,
  * `Mean`,
  * `Median`,
  * `Sum`,
  * `Count`,
  * `Last`
* [MORE](ref:reduce-operation)

### Math

* requirements
  * | time series

* allows
  * performing free-form math functions/operations | time series data and numbers

* uses | 
  * query / if series have SAME labels -> joined
  * expression's alert condition
    * _Example:_ [here](ref:dynamic-threshold-example)

* [MORE](ref:math-operation)

### Resample

Realigns a time range to a new set of timestamps, this is useful when comparing time series data from different data sources where the timestamps would otherwise not align.

For more details, refer to the [Resample documentation](ref:resample-operation).

### Threshold

Compares single numbers from previous queries or expressions (e.g., `$A`, `$B`) to a specified condition. It's often used to define the alert condition.

The threshold expression allows the comparison between two single values. Available threshold functions are:

- **Is above**: `$A > 5`
- **Is below**: `$B < 3`
- **Is equal to**: `$A == 2`
- **Is not equal to**: `$B =! 4`
- **Is above or equal to**: `$A >= 8`
- **Is below or equal to**: `$B <= 16`
- **Is within range**: `$A > 0 AND $A < 10`
- **Is outside range**: `$B < 0 OR $B > 100`
- **Is within range included**: `$A >= 0 AND $A <= 10`
- **Is outside range included**: `$B <= 0 OR $B >= 100`

A threshold returns `0` when the condition is false and `1` when true.

If the threshold is set as the alert condition, the alert fires when the threshold returns `1`.

### Recovery threshold

To reduce the noise from flapping alerts, you can set a recovery threshold so that the alert returns to the `Normal` or `Recovering` state only after the recovery threshold is crossed.

Flapping alerts occur when the query value repeatedly crosses above and below the alert threshold, causing frequent state changes. This results in a series of firing-resolved-firing notifications and a noisy alert state history.

For example, if you have an alert for latency with a threshold of 1000ms and the number fluctuates around 1000 (say 980 -> 1010 -> 990 -> 1020, and so on), then each of those might trigger a notification:

- 980 -> 1010 triggers a firing alert.
- 1010 -> 990 triggers a resolving alert.
- 990 -> 1020 triggers a firing alert again.

To prevent this, you can set a recovery threshold to define two thresholds instead of one:

1. An alert transitions to the `Pending` or `Alerting` state when it crosses the alert threshold.
1. It then transitions to the `Recovering` or `Normal` state only when it crosses the recovery threshold.

In the previous example, setting the recovery threshold to 900ms means the alert only resolves when the latency falls below 900ms:

- 980 -> 1010 triggers a firing alert.
- 1010 -> 990 does not resolve the alert, keeping it in the firing state.
- 990 -> 1020 keeps the alert in the firing state.

The recovery threshold mitigates unnecessary alert state changes and reduces alert noise.

{{< collapse title="Classic condition (legacy)" >}}

#### Classic condition (legacy)

Classic conditions exist mainly for compatibility reasons and should be avoided if possible.

Classic condition checks if any time series data matches the alert condition. It always produce one alert instance only, no matter how many time series meet the condition.

| Condition operators | How it works                                                                                                                                                                                                                                                |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `and`               | Two conditions before and after must be true for the overall condition to be true.                                                                                                                                                                          |
| `or`                | If one of conditions before and after are true, the overall condition is true.                                                                                                                                                                              |
| `logic-or`          | If the condition before `logic-or` is true, the overall condition is immediately true, without evaluating subsequent conditions. For instance, `TRUE and TRUE logic-or FALSE and FALSE` evaluate to `TRUE`, because the preceding condition returns `TRUE`. |

The following aggregation functions are also available to further refine your query.

| Function           | What it does                                                                    |
| ------------------ | ------------------------------------------------------------------------------- |
| `avg`              | Displays the average of the values                                              |
| `min`              | Displays the lowest value                                                       |
| `max`              | Displays the highest value                                                      |
| `sum`              | Displays the sum of all values                                                  |
| `count`            | Counts the number of values in the result                                       |
| `last`             | Displays the last value                                                         |
| `median`           | Displays the median value                                                       |
| `diff`             | Displays the difference between the newest and oldest value                     |
| `diff_abs`         | Displays the absolute value of diff                                             |
| `percent_diff`     | Displays the percentage value of the difference between newest and oldest value |
| `percent_diff_abs` | Displays the absolute value of `percent_diff`                                   |
| `count_non_null`   | Displays a count of values in the result set that aren't `null`                 |

{{< /collapse >}}
