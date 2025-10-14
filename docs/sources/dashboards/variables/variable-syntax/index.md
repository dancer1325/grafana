---
aliases:
  - ../../reference/templating/
  - ../../variables/advanced-variable-format-options/
  - ../../variables/syntax/
keywords:
  - grafana
  - templating
  - documentation
  - guide
  - template
  - variable
labels:
  products:
    - cloud
    - enterprise
    - oss
title: Variable syntax
description: Learn about different types of variable syntax
weight: 300
---

# Variable syntax

* variables' syntaxes
  - `$varname`
    - restrictions
      - ❌NOT valid | middle of a word❌
        - **Example:** apps.frontend.$server.requests.count
  - `${var_name}`
    - safer option
  - `${var_name:<format>}` OR `[[var_name:option]]`
    - allows
      - MORE control -- about -- how Grafana interpolates values
    - [variable format options](#advanced-variable-format-options)
  - `[[varname]]`
    - ❌NOT use❌
    - ⚠️deprecated⚠️

* BEFORE querying, variable interpolated /
  * 's value is _escaped_ -- to follow the -- syntax of the query language

## Advanced variable format options

* -- depends on the -- data source
* `glob` 
  * default/fallback option

* _Examples:_ [Grafana Playground](https://play.grafana.org/d/cJtIfcWiz/template-variable-formatting-options?orgId=1) 

### CSV

* `${var_name:csv}`
* allows
  * formating variables -- to -- MULTIPLE values / string comma-separated

* _Example:_ [here](https://play.grafana.org/d/cJtIfcWiz/template-variables-and-formatting-options?orgId=1&from=now-6h&to=now&timezone=utc&var-servers=$__all&var-TextVariable=Hello,%20world%21)
  * modify servers variable
  ```bash
  servers = ['test1', 'test2']
  String to interpolate: '${servers:csv}'
  Interpolation result: 'test1,test2'
  ```

### Distributed - OpenTSDB

* `${var_name:distributed}`
* allows
  * formatting variables -- to -- MULTIPLE values / OpenTSDB's custom format 

* _Example:_ [here](https://play.grafana.org/d/cJtIfcWiz/template-variables-and-formatting-options?orgId=1&from=now-6h&to=now&timezone=utc&var-servers=$__all&var-TextVariable=Hello,%20world%21)
  * modify servers variable
  ```bash
  servers = ['test1', 'test2']
  String to interpolate: '${servers:distributed}'
  Interpolation result: 'test1,servers=test2'
  ```

### Doublequote

* `${var_name:doublequote}`
* allows
  * formatting variables -- to -- MULTI-valued variables / comma-separated string `""` 
    * `"` is escaped -- by -- `\"`

* _Example:_ [here](https://play.grafana.org/d/cJtIfcWiz/template-variables-and-formatting-options?orgId=1&from=now-6h&to=now&timezone=utc&var-servers=$__all&var-TextVariable=Hello,%20world%21)
  * modify servers variable
  ```bash
  servers = ['test1', 'test2']
  String to interpolate: '${servers:doublequote}'
  Interpolation result: '"test1","test2"'
  ```

### Glob - Graphite

* `${var_name:glob}`
* allows
  * formatting variables -- to -- MULTIPLE values | glob (⚠️!=`:json`⚠️) 
* uses |
  * Graphite queries

* _Example:_ [here](https://play.grafana.org/d/cJtIfcWiz/template-variables-and-formatting-options?orgId=1&from=now-6h&to=now&timezone=utc&var-servers=$__all&var-TextVariable=Hello,%20world%21)
  * modify servers variable
  ```bash
  servers = ['test1', 'test2']
  String to interpolate: '${servers:glob}'
  Interpolation result: '{test1,test2}'
  ```

### Join

* `${var_name:join:yourDesiredDelimiter}`
* allows
  * formatting multi-valued variables / custom delimiter
    * default delimiter: `,`
  * _Example:_ 
  ```bash
  servers = ["test1", "test2"]
  String to interpolate: '${servers:join:&}'
  Interpolation result: "test1&test2"
  ```

### JSON

* `${var_name:json}`
* allows
  * formatting variables -- to -- MULTIPLE values as a comma-separated string

* _Example:_ [here](https://play.grafana.org/d/cJtIfcWiz/template-variables-and-formatting-options?orgId=1&from=now-6h&to=now&timezone=utc&var-servers=$__all&var-TextVariable=Hello,%20world%21)
  * modify servers variable
  ```bash
  servers = ['test1', 'test2']
  String to interpolate: '${servers:json}'
  Interpolation result: '["test1", "test2"]'
  ```

### Lucene - Elasticsearch

* `${var_name:json}`
* allows
  * formatting variables -- to -- MULTIPLE values / Lucene format

* _Example:_ [here](https://play.grafana.org/d/cJtIfcWiz/template-variables-and-formatting-options?orgId=1&from=now-6h&to=now&timezone=utc&var-servers=$__all&var-TextVariable=Hello,%20world%21)
  * modify servers variable
  ```bash
  servers = ['test1', 'test2']
  String to interpolate: '${servers:lucene}'
  Interpolation result: '("test1" OR "test2")'
  ```

### Percentencode

Formats single and multi valued variables for use in URL parameters.

```bash
servers = ['foo()bar BAZ', 'test2']
String to interpolate: '${servers:percentencode}'
Interpolation result: 'foo%28%29bar%20BAZ%2Ctest2'
```

### Pipe

* `${var_name:pipe}`
* allows
  * formatting variables -- to -- MULTIPLE values as a pipe-separated string
* _Example:_ [here](https://play.grafana.org/d/cJtIfcWiz/template-variables-and-formatting-options?orgId=1&from=now-6h&to=now&timezone=utc&var-servers=$__all&var-TextVariable=Hello,%20world%21)
  * modify servers variable
  ```bash
  servers = ['test1.', 'test2']
  String to interpolate: '${servers:pipe}'
  Interpolation result: 'test1.|test2'
  ```

### Query parameters

* `${var_name:queryparam}`
  * restrictions
    * ❌NOT valid | custom's ALL❌
  * allows
    * formatting single- and multi-valued variables -- to -- their query parameter representation
      * restriction 
        * ⚠️query parameter representation `var-<varName>=value`⚠️
          * 👀if you want to customize -> use `:customqueryparam`👀
  * _Example:_

    ```bash
    servers = ["test1", "test2"]
    String to interpolate: '${servers:queryparam}'
    Interpolation result: "var-servers=test1&var-servers=test2"
    ```

* `${var_name:customqueryparam:specifyParameterName:specifyValuePrefix}`
  * `specifyParameterName`
    * OPTIONAL
  * `specifyValuePrefix`
    * OPTIONAL
  * allows
    * customize how to format the query parameters 
  * _Example:_

  ```bash
  servers = ["test1", "test2"]
  String to interpolate: '${servers:customqueryparam:v-servers:x-}'
  Interpolation result: "v-servers=x-test1&v-servers=x-test2"
  ```

### Raw

Doesn't apply any data source-specific formatting to the variable.

For example, in this case, there's a dashboard with a Prometheus data source and a multi-value variable.
Grafana typically converts the variable values as follows to accommodate Prometheus:

```bash
servers = ['test1.', 'test2']
String to interpolate: '${servers}'
Interpolation result: '(test1 | test2)'
```

Using the raw format, the values are returned without that formatting:

```bash
servers = ['test1.', 'test2']
String to interpolate: '${servers:raw}'
Interpolation result: 'test1,test2'
```

### Regex

Formats variables with multiple values into a regex string.

```bash
servers = ['test1.', 'test2']
String to interpolate: '${servers:regex}'
Interpolation result: '(test1\.|test2)'
```

### Singlequote

* `${var_name:singlequote}`
  * allows
    * formatting single- and multi-valued variables -- to -- comma-separated string
      * if you need to escape
        * `'` -> by `\'`
        * `"` -> by `'`
  * _Example:_

  ```bash
  servers = ['test1', 'test2']
  String to interpolate: '${servers:singlequote}'
  Interpolation result: "'test1','test2'"
  ```

### Sqlstring

Formats single- and multi-valued variables into a comma-separated string, escapes `'` in each value by `''` and quotes each value with `'`.

```bash
servers = ["test'1", "test2"]
String to interpolate: '${servers:sqlstring}'
Interpolation result: "'test''1','test2'"
```

### Text

* `${var_name:text}`
  * allows
    * formatting single- and multi-valued variables -- to -- their text representation
      * single variable -> return the text representation
      * multi-valued variables -> return text representation -- joined by -- `+`
  * _Example:_

  ```bash
  servers = ["test1", "test2"]
  String to interpolate: '${servers:text}'
  Interpolation result: "test1 + test2"
  ```
