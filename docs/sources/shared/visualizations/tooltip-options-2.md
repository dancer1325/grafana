---
title: Tooltip options
comments: |
  There are three tooltip shared files, tooltip-options-1.md, tooltip-options-2.md, and tooltip-options-3.md, to cover the most common combinations of options. 
  Using shared files ensures that content remains consistent across visualizations that share the same options and users don't have to figure out which options apply to a specific visualization when reading that content. 
  This file is used in the following visualizations: time series, trend
---

* Tooltip options
  * == information / overlay | hover over | visualization's data points

| Option                                  | Description                                                                              |
|-----------------------------------------|------------------------------------------------------------------------------------------|
| [Tooltip mode](#tooltip-mode)           | == tooltips behave                                                                       |
| [Values sort order](#values-sort-order) | value order \| tooltip                                                                   |
| Hide zeros                              | if true -> series / `0` values, NOT displayed \| tooltip                                 |
| [Hover proximity](#hover-proximity)     | == how close (pixels) the cursor -- to a -- data point / trigger the tooltip |
| Max width                               | maximum width (\|pixels) of the tooltip box                                              |
| Max height                              | maximum height (\|pixels) of the tooltip box <br/> by default, 600 pixels                |

### Tooltip mode

* == how tooltips behave
  - **Single -**
    - shows ONLY 1! series (serie | you hover)
  - **All -** 
    - shows ALL visualization's series /
      - hovered over serie is bold highlighted
  - **Hidden -** 
    - NOT display the tooltip

### Values sort order

* requirements
  * **Tooltip mode** == **All**

* == values order | tooltip
  - **None**
    - Grafana AUTOMATICALLY sorts
  - **Ascending**
    - from smallest to largest
  - **Descending**
    - from largest to smallest

### Hide zeros

* requirements
  * **Tooltip mode** == **All**
