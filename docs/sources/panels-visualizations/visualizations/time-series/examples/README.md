# default way / show the variations of a set of data values | time
* `docker run -d -p 3000:3000 grafana/grafana`
* http://localhost:3000/
* admin / admin
* **Dashboards** > **New** > **Add visualization** > preselect the time series

# if there are >1 numerical data -> EACH one is plotted | NEW line, point, or bar labeled
* [link](https://play.grafana.org/d/000000016/time-series-graphs?orgId=1&from=2025-10-10T06:26:43.638Z&to=2025-10-10T07:26:43.638Z&timezone=browser&editPanel=1&viewPanel=panel-1)

# Supported data formats
## Example 1

* 3 numeric fields / represented by 3 lines

| Time                | value1 | value2 | value3 |
| ------------------- | ------ | ------ | ------ |
| 2022-11-01 10:00:00 | 1      | 2      | 3      |
| 2022-11-01 11:00:00 | 4      | 5      | 6      |
| 2022-11-01 12:00:00 | 7      | 8      | 9      |
| 2022-11-01 13:00:00 | 4      | 5      | 6      |

![](/grafana/media/docs/panels-visualizations/screenshot-grafana-11.1-timeseries-example1v2.png)

* [here](https://play.grafana.org/goto/af0m4sjm36vi8c?orgId=1)
  * see table-related

## Example 2

The time series visualization also supports multiple datasets
* If all datasets are in the correct format, the visualization plots the numeric fields of all datasets and labels them using the column name of the field.

### Query1

| Time                | value1 | value2 | value3 |
| ------------------- | ------ | ------ | ------ |
| 2022-11-01 10:00:00 | 1      | 2      | 3      |
| 2022-11-01 11:00:00 | 4      | 5      | 6      |
| 2022-11-01 12:00:00 | 7      | 8      | 9      |

### Query2

| timestamp           | number1 | number2 | number3 |
| ------------------- | ------- | ------- | ------- |
| 2022-11-01 10:30:00 | 11      | 12      | 13      |
| 2022-11-01 11:30:00 | 14      | 15      | 16      |
| 2022-11-01 12:30:00 | 17      | 18      | 19      |
| 2022-11-01 13:30:00 | 14      | 15      | 16      |

![Time series line chart with two datasets](/grafana/media/docs/panels-visualizations/screenshot-grafana-11.1-timeseries-example2v2.png)

## Example 3

If you want to more easily compare events between different, but overlapping, time frames, you can do this by using a time offset while querying the compared dataset:

### Query1

| Time                | value1 | value2 | value3 |
| ------------------- | ------ | ------ | ------ |
| 2022-11-01 10:00:00 | 1      | 2      | 3      |
| 2022-11-01 11:00:00 | 4      | 5      | 6      |
| 2022-11-01 12:00:00 | 7      | 8      | 9      |

### Query2

| timestamp(-30min)   | number1 | number2 | number3 |
| ------------------- | ------- | ------- | ------- |
| 2022-11-01 10:30:00 | 11      | 12      | 13      |
| 2022-11-01 11:30:00 | 14      | 15      | 16      |
| 2022-11-01 12:30:00 | 17      | 18      | 19      |
| 2022-11-01 13:30:00 | 14      | 15      | 16      |

![Time Series Example with second Data Set offset](/media/docs/grafana/panels-visualizations/screenshot-grafana-11.1-timeseries-example3v2.png 'Time Series Example with second Data Set offset')

When you add the offset, the resulting visualization makes the datasets appear to be occurring at the same time so that you can compare them more easily.
