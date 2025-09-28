---
aliases:
  - ../basics/exemplars/
  - ../basics/exemplars/view-exemplars/
description: Introduction to exemplars
keywords:
  - grafana
  - concepts
  - exemplars
  - prometheus
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Exemplars
title: Introduction to exemplars
weight: 800
---

# Introduction to exemplars

* exemplar
  * == specific trace / measured | time interval
  * allows
    * link metrics -- & -- traces
    * isolate problems
  * supported ONLY | Prometheus
  * [how to configure exemplars | Prometheus?](../../datasources/prometheus/_index.md#exemplars)
  * displayed
    * |
      * Explore view
      * dashboards
      * Loki log details
    * -- as a -- highlighted star

* metrics
  * give you
    * aggregated view of your system
* traces
  * give you
    * fine grained view of 1! request

* compare traceS

![](/grafana/media/docs/exemplars/screenshot-exemplars.png)

* [enable Grafana Tempo’s distributed tracing | massive scale](/blog/2021/03/31/intro-to-exemplars-which-enable-grafana-tempos-distributed-tracing-at-massive-scale/)

## View exemplar data

### In Explore

* exemplar | Explore
  * == highlighted stars + metrics data
  * [tracing | Explore](../../explore/trace-integration.md)

* TODO: To examine the details of an exemplar trace:

1. Place your cursor over an exemplar (highlighted star).
   Depending on the trace data source you are using, you may see a blue button with the label `Query with <DATA SOURCE NAME>`.
   In the following example, the tracing data source is Tempo.

   {{< figure src="/media/docs/grafana/exemplars/screenshot-exemplar-details.png" class="docs-image--no-shadow" max-width= "350px" caption="Screenshot showing exemplar details" >}}

1. Click the **Query with Tempo** option next to the `traceID` property.
   The trace details, including the spans within the trace are listed in a separate panel on the right.

   {{< figure src="/media/docs/grafana/exemplars/screenshot-exemplar-explore-view.png" class="docs-image--no-shadow" max-width= "900px" caption="Explorer view with panel showing trace details" >}}

* [analyze trace & span details](#analyze-trace-and-spans)

### In logs

You can also view exemplar trace details from the Loki logs in Explore.
Use regular expressions within the Derived fields links for Loki to extract the `traceID` information.
Now when you expand Loki logs, you can see a `traceID` property under the **Detected fields** section.
To learn more about how to extract a part of a log message into an internal or external link, refer to [using derived fields in Loki](../../explore/logs-integration/).

To view the details of an exemplar trace:

1. Expand a log line and scroll down to the `Fields` section.
   Depending on your backend trace data source, you may see a blue button with the label `<DATA SOURCE NAME>`.

1. Click the blue button next to the `traceID` property.
   Typically, it has the name of the backend data source.
   In the following example, the tracing data source is Tempo.
   The trace details, including the spans within the trace are listed in a separate panel on the right.

{{< figure src="/media/docs/grafana/exemplars/screenshot-exemplar-loki-logs.png" class="docs-image--no-shadow" max-width= "750px" caption="Explorer view with panel showing trace details" >}}

For more information on how to drill down and analyze the trace and span details, refer to the [Analyze trace and span details](#analyze-trace-and-spans) section.

### Analyze trace and spans

This panel shows the details of the trace in different segments.

- The top segment displays the trace ID to indicate that the query results correspond to the specific trace.

  You can add more traces to the results using the `Add query` button.

- The next segment shows the entire span for the specific trace as a narrow strip.
  All levels of the trace from the client all the way down to database query is displayed, which provides a bird's eye view of the time distribution across all layers over which the HTTP request was processed.
  1. You can click within this strip view to display a magnified view of a smaller time segment within the span. This magnified view shows up in the bottom segment of the panel.

  1. In the magnified view, you can expand or collapse the various levels of the trace to drill down to the specific span of interest.

     For example, if the strip view shows that most of the latency was within the app layer, you can expand the trace down the app layer to investigate the problem further.
     To expand a particular layer of span, click the left icon.
     The same button can collapse an expanded span.

- To see the details of the span at any level, click the span itself.

  This displays additional metadata associated with the span.
  The metadata itself is initially shown in a narrow strip but you can see more details by clicking the metadata strip.

  {{< figure src="/media/docs/grafana/exemplars/screenshot-exemplar-span-details.png" class="docs-image--no-shadow" max-width= "600px" caption="Span details" >}}
