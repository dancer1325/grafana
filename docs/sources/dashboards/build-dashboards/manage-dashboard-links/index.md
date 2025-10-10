---
aliases:
  - ../../features/navigation-links/
  - ../../linking/
  - ../../linking/dashboard-links/
  - ../../linking/linking-overview/
  - ../../panels/working-with-panels/add-link-to-panel/
  - ../manage-dashboard-links/
description: Add links to your Grafana dashboards to connect to other dashboards, panels, and websites
keywords:
  - link
  - dashboard
  - grafana
  - linking
  - create links
  - link dashboards
  - navigate
labels:
  products:
    - cloud
    - enterprise
    - oss
menuTitle: Manage dashboard links
title: Manage dashboard links
weight: 200
refs:
  data-links:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-data-links/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-data-links/
  data-link-variables:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/panels-visualizations/configure-data-links/#data-link-variables
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/panels-visualizations/configure-data-links/#data-link-variables
  dashboard-url-variables:
    - pattern: /docs/grafana/
      destination: /docs/grafana/<GRAFANA_VERSION>/dashboards/build-dashboards/create-dashboard-url-variables/
    - pattern: /docs/grafana-cloud/
      destination: /docs/grafana-cloud/visualizations/dashboards/build-dashboards/create-dashboard-url-variables/
---

# Manage dashboard links

* allows
  * creating shortcuts - to -- OTHER dashboards, panels, and external websites 
* types
  * dashboard links, 
    * displayed | top of the dashboard
    * use cases
      * link | external site
      * ALL or MOST dashboard' pannels
  * panel links,
    * accessible -- via -- icon | panel title 
    * use cases
      * link | external site
      * specific panel
  * data links
    * use cases
      * specific series
      * 1! measurement
* uses
  * navigation BETWEEN dashboards
  * connect others -- to -- your visualizations

## Controlling time range using the URL

* | dashboard URL,
  * add query parameters
    - `from`
      - time range's lower limit
      - | ms epoch
    - `to`
      - time range's upper limit
      - | ms epoch
    - `time` and `time.window`
      - == `from=time-time.window/2&to=time+time.window/2`
      - BOTH | ms

## Dashboard links

* allows
  * specifying the time range & current template variables

* _Example:_ [Dashboard links with variables](https://play.grafana.org/d/rUpVRdamz/dashboard-links-with-variables?orgId=1)
  * variables ALSO set

### Add links to dashboards

* allows
  * | top of your current dashboard,
    * add links -- to -- other dashboards 

![](/grafana/media/docs/dashboards/addUrlLinkToADashboard.png)

1. | dashboard / you want to link,
   1. **Edit** > **Settings** > **Links** tab and then click **Add dashboard link**
      1. by default, link type == **Dashboards**
      1. | **With tags** drop-down,
         1. tags / limit the linked dashboards
            1. if you do NOT add any tags -> Grafana includes links to ALL OTHER dashboards
      1. link options
         - **Show as dropdown**
           - use case
             - you link to lots of dashboards
           - Otherwise, Grafana displays the dashboard links side by side | top of your dashboard
         - **Include current time range** 
           - include the dashboard time range | link
           - if the user clicks the link -> the linked dashboard opens / indicated time range ALREADY set
           - **Example:** [here](https://play.grafana.org/d/000000010/annotations?orgId=1&from=now-3h&to=now)
         - **Include current template variable values** 
           - include template variables currently used -- as -- query parameters | link
             - any matching templates | linked dashboard -> set to the values | link
           - [Dashboard URL variables](ref:dashboard-url-variables)
         - **Open link in new tab**
   1. **Save dashboard** > **Back to dashboard** > **Exit edit**

### Add a URL link to a dashboard

* ALLOWED links -- to -- any URL (dashboards, panels, or external sites)

1. | dashboard / you want to link
   1. **Edit** > **Settings** > **Links** tab > **Add dashboard link**
      1. **Type** drop-down == **Link**.
      1. set **URL** == URL / you want to link
      1. **Tooltip** field
         1. == tooltip / displayed | user hovers their mouse | it
      1. **Icon** drop-down
         2. == icon / displayed with the link
      1. link options
         -  by default, are enabled -- for -- URL links
         - **Include current time range** 
           - [here](#add-links-to-dashboards)
         - **Include current template variable values** 
           - [here](#add-a-url-link-to-a-dashboard)
         - **Open link in new tab**
   1. **Save dashboard** > **Back to dashboard** > **Exit edit**

### Update a dashboard link

To edit, duplicate, or delete dashboard link, follow these steps:

1. In the dashboard you want to link, click **Edit**.
1. Click **Settings**.
1. Go to the **Links** tab.
1. Do one of the following:
   - **Edit** - Click the name of the link and update the link settings.
   - **Duplicate** - Click the copy link icon next to the link that you want to duplicate.
   - **Delete** - Click the red **X** next to the link that you want to delete, and then **Delete**.

1. Click **Save dashboard**.
1. Click **Back to dashboard** and then **Exit edit**.

## Panel links

Each panel can have its own set of links that are shown in the upper left of the panel after the panel title. You can link to any available URL, including dashboards, panels, or external sites. You can even control the time range to ensure the user is zoomed in on the right data in Grafana.

Click the icon next to the panel title to see available panel links.

{{< figure src="/media/docs/grafana/dashboards/screenshot-panel-links-v11.3.png" max-width="550px" alt="List of panel links displayed" >}}

### Add a panel link

1. Hover over any part of the panel to which you want to add the link to display the actions menu on the top right corner.
1. Click the menu and select **Edit**.

   To use a keyboard shortcut to open the panel, hover over the panel and press `e`.

1. Expand the **Panel options** section, scroll down to **Panel links**.
1. Click **Add link**.
1. Enter a **Title**. **Title** is a human-readable label for the link that will be displayed in the UI.
1. Enter the **URL** you want to link to.
   You can even add one of the template variables defined in the dashboard. Press Ctrl+Space or Cmd+Space and click in the **URL** field to see the available variables. By adding template variables to your panel link, the link sends the user to the right context, with the relevant variables already set. You can also use time variables:
   - `from` - Defines the lower limit of the time range, specified in ms epoch.
   - `to` - Defines the upper limit of the time range, specified in ms epoch.
   - `time` and `time.window` - Define a time range from `time-time.window/2` to `time+time.window/2`. Both params should be specified in ms. For example `?time=1500000000000&time.window=10000` will result in 10s time range from 1499999995000 to 1500000005000.
1. If you want the link to open in a new tab, then select **Open in new tab**.
1. Click **Save** to save changes and close the dialog box.
1. Click **Save dashboard** in the top-right corner.
1. Click **Back to dashboard** and then **Exit edit**.

### Update a panel link

1. Hover over any part of the panel to display the actions menu on the top right corner.
1. Click the menu and select **Edit**.

   To use a keyboard shortcut to open the panel, hover over the panel and press `e`.

1. Expand the **Panel options** section, scroll down to Panel links.
1. Find the link that you want to make changes to.
1. Click the Edit (pencil) icon to open the Edit link window.
1. Make any necessary changes.
1. Click **Save** to save changes and close the dialog box.
1. Click **Save dashboard** in the top-right corner.
1. Click **Back to dashboard** and then **Exit edit**.

### Delete a panel link

1. Hover over any part of the panel to display the actions menu on the top right corner.
1. Click the menu and select **Edit**.

   To use a keyboard shortcut to open the panel, hover over the panel and press `e`.

1. Expand the **Panel options** section, scroll down to Panel links.
1. Find the link that you want to delete.
1. Click the **X** icon next to the link you want to delete.
1. Click **Save dashboard** in the top-right corner.
1. Click **Back to dashboard** and then **Exit edit**.
