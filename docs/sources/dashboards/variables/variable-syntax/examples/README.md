* goal
  * build [this dashboard](https://play.grafana.org/d/cJtIfcWiz/template-variables-and-formatting-options?orgId=1&from=now-6h&to=now&timezone=utc&var-servers=$__all&var-TextVariable=Hello,%20world%21) -- from -- scratch

* `docker run -d --name grafana -p 3000:3000 grafana/grafana`
* http://localhost:3000/
  * admin/admin
* Dashboard > New Dashboard > Add visualization > Text

```markdown
# Template Variable Formatting Options

Syntax: `${var_name:option}`

Change the `servers` variable above to test the interpolation for the different formatting options in the table below.

[Documentation for advanced formatting](https://grafana.com/docs/grafana/latest/dashboards/variables/variable-syntax/#advanced-variable-format-options)

## Live Examples

<table>
    <tr>
        <td>Filter Option</td>
        <td>Example</td>
        <td>Interpolated</td>
        <td>Description</td>
    </tr>
    <tr>
        <td><code> glob </code> </td>
        <td> <code>${var_name:glob}</code></td>
        <td> ${servers:glob}</td>
        <td> (Default) Formats multi-value variable into a glob (for Graphite queries) </td>
    </tr>
    </tr>
     <tr>
        <td><code> regex </code> </td>
        <td> <code>${var_name:regex}</code></td>
        <td> ${servers:regex}</td>
        <td>  Formats multi-value variable into a regex string </td>
    </tr>
    </tr>
     <tr>
        <td><code> pipe </code> </td>
        <td> <code>${var_name:pipe}</code></td>
        <td> ${servers:pipe}</td>
        <td> Formats multi-value variable into a pipe-separated string</td>
    </tr>
    <tr>
        <td><code> csv </code> </td>
        <td> <code>${var_name:csv}</code></td>
        <td> ${servers:csv}</td>
        <td> Formats multi-value variable into a comma-separated string </td>
    </tr>
    <tr>
        <td><code> distributed </code> </td>
        <td> <code>${var_name:distributed}</code></td>
        <td> ${servers:distributed}</td>
        <td> Formats multi-value variable in custom format for OpenTSDB. </td>
    </tr>
    <tr>
        <td><code> lucene </code> </td>
        <td> <code>${var_name:lucene}</code></td>
        <td> ${servers:lucene}</td>
        <td> Formats multi-value variable as lucene expression </td>
    <tr>
        <td><code> raw </code> </td>
        <td> <code>${var_name:raw}</code></td>
        <td> ${servers:raw}</td>
        <td>  Turns off data source specific formatting (like single quotes in an SQL query) </td>
    </tr>
</table>

Additonal cases

<table>
    </tr>
        <tr>
        <td><code> json </code> </td>
        <td> <code>${var_name:json}</code></td>
        <td> ${extra:json}</td>
        <td> Formats multi-value variable as json </td>
    </tr>
    </tr>
        <tr>
        <td><code> doublequote </code> </td>
        <td> <code>${var_name:doublequote}</code></td>
        <td> ${extra:doublequote}</td>
        <td> Formats multi-value variable as doublequote </td>
    </tr>
    </tr>
        <tr>
        <td><code> join:yourDesiredDelimiter </code> </td>
        <td> <code>${var_name:join:yourDesiredDelimiter}</code></td>
        <td> ${extra:join:&}</td>
        <td> Formats multi-value variable joined by your desired delimiter </td>
    </tr>
    </tr>
        <tr>
        <td><code> queryparam </code> </td>
        <td> <code>${var_name:queryparam}</code></td>
        <td> ${extra:queryparam}</td>
        <td> Formats single OR multi-value variable to their query parameter representation </td>
    </tr>
    </tr>
        <tr>
        <td><code> customqueryparam </code> </td>
        <td> <code>${var_name:customqueryparam:paramName:valueprefix}</code></td>
        <td> ${extra:customqueryparam:vserversP:xP-}</td>
        <td> Formats single OR multi-value variable to format the query parameters </td>
    </tr>
    </tr>
        <tr>
        <td><code> singlequote </code> </td>
        <td> <code>${var_name:singlequote}</code></td>
        <td> ${extra:singlequote}</td>
        <td> Formats single OR multi-value variable to comma-separated string </td>
    </tr>
    </tr>
        <tr>
        <td><code> text </code> </td>
        <td> <code>${var_name:text}</code></td>
        <td> ${extra:text}</td>
        <td> Formats single OR multi-value variable to their text representation </td>
    </tr>
</table>
```

* Dashboard > Settings > Variables >
  * First one
    * General > Name == servers
    * Variable Type == Custom
    * Custom options == `test.1, test.2, test.3`
    * Select options > 
      * Multi-value
      * Include ALL option 
        * \> Custom all value
          * ⚠️NOT add anything⚠️
          * ❌if you include  == `test.1, test.2, test.3` -> formatting NOT valid❌
  * Second one
    * General > Name == specificForJson
    * Variable Type == Custom
    * Custom options == `test1, test2, test3`
    * Select options >
      * Multi-value
      * Include ALL option 
        * \> Custom all value
          * ⚠️NOT add anything⚠️
          * ❌if you include  == `test1, test2, test3` -> formatting NOT valid❌
