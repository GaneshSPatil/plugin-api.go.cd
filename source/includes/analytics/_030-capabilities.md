## Get Plugin Capabilities

This message is a request to the plugin to provide plugin capabilities. Based on these capabilities GoCD would enable or disable the plugin features for a user.

<p class='request-name-heading'>Request name</p>

`go.cd.analytics.get-capabilities`

<p class='request-body-heading'>Request body</p>

Server sends request with `Empty` request body.

<p class='response-code-heading'>Response Body</p>

> An example response body —

```json
{
    "supported_analytics": [
        {
            "id": "pipeline_duration",
            "title": "Pipeline Duration",
            "type": "pipeline"
        },
        {
            "id": "pipelines_with_longest_average_wait_time",
            "title": "Pipelines With The Longest Average Wait Times",
            "type": "dashboard"
        }
    ]
}
```

The response body will contain the <code>supported_analytics</code> field which is a collection of analytics metrics.Each analytics metric has following JSON elements:

<p class='attributes-table-follows'></p>

| Key     | Type     | Description                                                                                                                                                                                       |
|---------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `id`    | `String` | The unique id of the analytics metric.                                                                                                                                                            |
| `title` | `String` | The unique title of the analytics metric.                                                                                                                                                         |
| `type`  | `String` | The type of the analytics metric. The type field is used to identify the scope of the analytics metric. The analytics metric will be displayed in the core GoCD application in the defined scope. |

Valid types of analytics metric are as follows:

<p class='attributes-table-follows'></p>

| Type        | Scope                                                                                    |
|-------------|------------------------------------------------------------------------------------------|
| `dashboard` | Dashboard level analytics will be displayed at the global level in the GoCD application. |
| `pipeline`  | Pipeline level analytics will be displayed on each pipeline in the GoCD application.     |

<aside class="info">
  <strong>Note</strong>: Any other analytics type apart from above mentioned types will be ignored.
</aside>


The plugin is expected to return status `200` if it can understand the request.
