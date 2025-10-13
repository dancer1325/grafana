---
aliases:
  - ../../best-practices/
  - ../../best-practices/best-practices-for-creating-dashboards/
  - ../../best-practices/best-practices-for-managing-dashboards/
  - ../../best-practices/common-observability-strategies/
  - ../../best-practices/dashboard-management-maturity-levels/
  - ../../getting-started/strategies/
description: Learn best practices for building and maintaining Grafana dashboards
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Best practices
title: Grafana dashboard best practices
weight: 800
refs:
  text-panel:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/text/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/text/
  text-panel-visualization:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/text/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/text/
  data-sources:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/datasources/
  url-parameters:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-data-links/#data-link-variables
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-data-links/#data-link-variables
  variable-examples:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/variables/#examples-of-templates-and-variables
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/variables/#examples-of-templates-and-variables
  dashboard-list-panel:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/dashboard-list/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/visualizations/dashboard-list/
  manage-dashboard-links:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/build-dashboards/manage-dashboard-links/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/build-dashboards/manage-dashboard-links/
  usage-insights:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/assess-dashboard-usage/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/assess-dashboard-usage/
  templates-and-variables:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/variables/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/variables/
  thresholds:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-thresholds/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-thresholds/
---

# Grafana dashboard best practices

* audience
  * Grafana administrators
  * how to build & maintain Grafana dashboards

## Common observability strategies

* == what to monitor
* allows you to
  * make uniform dashboards
  * scale your observability platform MORE easily

### Guidelines for usage

- USE 
  - method
    - tells you
      - how happy your machines are
  - 👀reports | causes of issues👀
- RED 
  - method
    - tells you
      - how happy your users are
  - 👀reports | user experience 
    - == symptoms of problems👀

### USE method

* USE ==
  - **Utilization**
    - Percent time / resource is busy
      - _Example:_ node CPU usage
  - **Saturation**
    - work / resource has to do
      - _Example:_ queue length OR node load
  - **Errors**
    - Count of error events

* use cases
  * hardware resources | infrastructure
    * _Example:_ CPU, memory, and network devices

* MORE [USE Method](http://www.brendangregg.com/usemethod.html)
* _Example:_ TODO:

### RED method

* RED ==
  - **Rate**
    - Requests / second
  - **Errors** 
    - NUMBER of requests / are failing
  - **Duration** 
    - time / these requests take

* use cases
  * services
  * alerting & SLAs 

* RED dashboard
  * == proxy -- for -- user experience

* [The RED method: How to instrument your services](https://grafana.com/blog/2018/08/02/the-red-method-how-to-instrument-your-services)
* _Example:_ TODO:

### The Four Golden Signals

* == user-facing system's metrics 
  * _Examples of user-facing system:_ web, API, app, ...

* == RED method + saturation

- **Latency -**
  - time taken -- to -- serve a request
- **Traffic -** 
  - how much demand | your system
- **Errors -** 
  - rate of requests / are failing
- **Saturation -** 
  - how "full" your system is

* see [Google SRE handbook](https://landing.google.com/sre/sre-book/chapters/monitoring-distributed-systems/#xref_monitoring_golden-signals)

* _Example:_ [here](https://play.grafana.org/d/000000109/)

## Dashboard management maturity model

* _Dashboard management maturity_ 
  * == how well-designed & efficient your dashboard ecosystem is

* [Fool-Proof Kubernetes Dashboards for Sleep-Deprived Oncalls](https://www.youtube.com/watch?v=YE2aQFiMGfY)

### Low - default state

* NO coherent dashboard management strategy

* symptoms to be here
  - everyone can modify your dashboards
  - copied dashboards
    - == NO dashboard reuse
  - NO version control
  - NO alerts / direct you -- to the -- right dashboard

### Medium - methodical dashboards

* symptoms to be here
  - prevent duplicated dashboards -- via -- template variables
    - Even better, you can make the data source a template variable too, so you can reuse the same dashboard across different clusters and monitoring backends.

      Refer to the list of [Variable examples](ref:variable-examples) if you want some ideas.

- Methodical dashboards according to an [observability strategy](#common-observability-strategies).
- Hierarchical dashboards with drill-downs to the next level.


- Dashboard design reflects service hierarchies. The example shown below uses the RED method (request and error rate on the left, latency duration on the right) with one row per service. The row order reflects the data flow.

  {{< figure class="float-right"  max-width="100%" src="/static/img/docs/best-practices/service-hierarchy-example.png" caption="Example of a service hierarchy" >}}

- Compare like to like: split service dashboards when the magnitude differs. Make sure aggregated metrics don't drown out important information.
- Expressive charts with meaningful use of color and normalizing axes where you can.
  - Example of meaningful color: Blue means it's good, red means it's bad. [Thresholds](ref:thresholds) can help with that.
  - Example of normalizing axes: When comparing CPU usage, measure by percentage rather than raw number, because machines can have a different number of cores. Normalizing CPU usage by the number of cores reduces cognitive load because the viewer can trust that at 100% all cores are being used, without having to know the number of CPUs.
- Directed browsing cuts down on "guessing."
  - Template variables make it harder to "just browse" randomly or aimlessly.
  - Most dashboards should be linked to by alerts.
  - Browsing is directed with links. For more information, refer to [Manage dashboard links](ref:manage-dashboard-links).
- Version-controlled dashboard JSON.

### High - optimized use

At this stage, you have optimized your dashboard management use with a consistent and thoughtful strategy. It requires maintenance, but the results are worth it.

- Actively reducing sprawl.
  - Regularly review existing dashboards to make sure they are still relevant.
  - Only approved dashboards added to master dashboard list.
  - Tracking dashboard use. If you're an Enterprise user, you can take advantage of [Usage insights](ref:usage-insights).
- Consistency by design.
- Use scripting libraries to generate dashboards, ensure consistency in pattern and style.
  - grafonnet (Jsonnet)
  - grafanalib (Python)
- No editing in the browser. Dashboard viewers change views with variables.
- Browsing for dashboards is the exception, not the rule.
- Perform experimentation and testing in a separate Grafana instance dedicated to that purpose, not your production instance. When a dashboard in the test environment is proven useful, then add that dashboard to your main Grafana instance.

## Best practices for creating dashboards

This page outlines some best practices to follow when creating Grafana dashboards.

### Before you begin

Here are some principles to consider before you create a dashboard.

#### A dashboard should tell a story or answer a question

What story are you trying to tell with your dashboard? Try to create a logical progression of data, such as large to small or general to specific. What is the goal for this dashboard? (Hint: If the dashboard doesn't have a goal, then ask yourself if you really need the dashboard.)

Keep your graphs simple and focused on answering the question that you are asking. For example, if your question is "which servers are in trouble?", then maybe you don't need to show all the server data. Just show data for the ones in trouble.

#### Dashboards should reduce cognitive load, not add to it

<!-- vale Grafana.GoogleWill = NO -->

_Cognitive load_ is basically how hard you need to think about something in order to figure it out. Make your dashboard easy to interpret. Other users and future you (when you're trying to figure out what broke at 2 AM) will appreciate it.

Ask yourself:

- Can I tell what exactly each graph represents? Is it obvious, or do I have to think about it?
- If I show this to someone else, how long will it take them to figure it out? Will they get lost?

<!-- vale Grafana.GoogleWill = YES -->

#### Have a monitoring strategy

It's easy to make new dashboards. It's harder to optimize dashboard creation and adhere to a plan, but it's worth it. This strategy should govern both your overall dashboard scheme and enforce consistency in individual dashboard design.

Refer to [Common observability strategies](#common-observability-strategies) and [Dashboard management maturity levels](#dashboard-management-maturity-model) for more information.

#### Write it down

Once you have a strategy or design guidelines, write them down to help maintain consistency over time. Check out this [Wikimedia runbook example](https://wikitech.wikimedia.org/wiki/Performance/Runbook/Grafana_best_practices).

### Best practices to follow

- When creating a new dashboard, make sure it has a meaningful name.
  - If you are creating a dashboard to play or experiment, then put the word `TEST` or `TMP` in the name.
  - Consider including your name or initials in the dashboard name or as a tag so that people know who owns the dashboard.
  - Remove temporary experiment dashboards when you are done with them.
- If you create many related dashboards, think about how to cross-reference them for easy navigation. Refer to [Best practices for managing dashboards](#best-practices-for-managing-dashboards) for more information.
- Grafana retrieves data from a data source. A basic understanding of [data sources](ref:data-sources) in general and your specific is important.
- Avoid unnecessary dashboard refreshing to reduce the load on the network or backend. For example, if your data changes every hour, then you don't need to set the dashboard refresh rate to 30 seconds.
- Use the left and right Y-axes when displaying time series with different units or ranges.
- Add documentation to dashboards and panels.
  - To add documentation to a dashboard, add a [Text panel visualization](ref:text-panel-visualization) to the dashboard. Record things like the purpose of the dashboard, useful resource links, and any instructions users might need to interact with the dashboard. Check out this [Wikimedia example](https://grafana.wikimedia.org/d/000000066/resourceloader?orgId=1).
  - To add documentation to a panel, edit the panel settings and add a description. Any text you add appears if you hover your cursor over the small `i` in the top left corner of the panel.
- Reuse your dashboards and enforce consistency by using [templates and variables](ref:templates-and-variables).
- Be careful with stacking graph data. The visualizations can be misleading, and hide important data. It's recommended that you turn it off in most cases.

## Best practices for managing dashboards

This page outlines some best practices to follow when managing Grafana dashboards.

### Before you begin

Here are some principles to consider before you start managing dashboards.

#### Strategic observability

There are several [common observability strategies](#common-observability-strategies). You should research them and decide whether one of them works for you or if you want to come up with your own. Either way, have a plan, write it down, and stick to it.

Adapt your strategy to changing needs as necessary.

#### Maturity level

What is your dashboard maturity level? Analyze your current dashboard setup and compare it to the [Dashboard management maturity model](#dashboard-management-maturity-model). Understanding where you are can help you decide how to get to where you want to be.

### Best practices to follow

- Avoid dashboard sprawl, meaning the uncontrolled growth of dashboards. Dashboard sprawl negatively affects time to find the right dashboard. Duplicating dashboards and changing "one thing" (worse: keeping original tags) is the easiest kind of sprawl.
  - Periodically review the dashboards and remove unnecessary ones.
  - If you create a temporary dashboard, perhaps to test something, prefix the name with `TEST:`. Delete the dashboard when you are finished.
- Copying dashboards with no significant changes is not a good idea.
  - You miss out on updates to the original dashboard, such as documentation changes, bug fixes, or additions to metrics.
  - In many cases copies are being made to simply customize the view by setting template parameters. This should instead be done by maintaining a link to the master dashboard and customizing the view with [URL parameters](ref:url-parameters).
- When you must copy a dashboard, clearly rename it and _do not_ copy the dashboard tags. Tags are important metadata for dashboards that are used during search. Copying tags can result in false matches.
- Maintain a dashboard of dashboards or cross-reference dashboards. This can be done in several ways:
  - Create dashboard links, panel, or data links. Links can go to other dashboards or to external systems. For more information, refer to [Manage dashboard links](ref:manage-dashboard-links).
  - Add a [Dashboard list panel](ref:dashboard-list-panel). You can then customize what you see by doing tag or folder searches.
  - Add a [Text panel](ref:text-panel) and use markdown to customize the display.
