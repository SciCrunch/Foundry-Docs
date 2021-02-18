# Foundry API: Source Information

{% api-method method="get" host="https://foundry-dev.scicrunch.io/foundry/api" path="/sources" %}
{% api-method-summary %}
sources
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get free cakes.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apiKey" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
_Response Body_: \(`A JSON array of JSON objects one per source`\).
{% endapi-method-response-example-description %}

```
[
  {
    "sourceID": "SCR_013869-Cellosaurus-RIN-test",
    "name": "RIN - Cell Lines",
    "dataSource": "SCR_013869-Cellosaurus-RIN-test",
    "repositoryID": "",
    "transformScript": "",
    "primaryKeyJSONPath": ["$.'pr_scr_013869_1'.'e_uid'"],
    "scrID": "",
    "itemType": "",
    "dataModel": "",
    "mappingFile": "",
    "lastModified": "",
    "id": 0
  },
  {
    "sourceID": "nif-0000-00018-2",
    "name": "BAMS",
    "dataSource": "nif-0000-00018-2",
    "repositoryID": "",
    "transformScript": "<transformation-script>",
    "primaryKeyJSONPath": ["$.pr_nif_0000_00018_2.v_uuid"],
    "scrID": "",
    "itemType": "",
    "dataModel": "",
    "mappingFile": "",
    "lastModified": "",
    "id": 1
  }
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Unauthorized request
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
Server Error
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://foundry-dev.scicrunch.io" path="/sources/source" %}
{% api-method-summary %}
sources/source
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="sourceID" type="string" required=true %}
Source Identifier
{% endapi-method-parameter %}

{% api-method-parameter name="dataSource" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="apiKey" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
_Response Body_: \(`A JSON object`\)
{% endapi-method-response-example-description %}

```
{
  "name": "RIN - Cell Lines",
  "sourceID": "SCR_013869-Cellosaurus-RIN",
  "dataSource": "SCR_013869-Cellosaurus-RIN",
  "repositoryID": "",
  "params": {
    "ignoreLines": "1",
    "keepMissing": "false",
    "escapeCharacter": "&#092;",
    "textQuote": "&#034;",
    "delimiter": ",",
    "useCache": "false",
    "headerLine": "1",
    "ingestURL": "file:///home/bozyurt/dev/java/Foundry-ES/test/Cell_lines_Testing.csv"
  },
  "type": "csv",
  "scrID": "",
  "itemType": "",
  "dataModel": "",
  "mappingFile": "",
  "lastModified": "Fri Dec 20 13:54:00 PST 2019"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Unauthorized Request
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
Server Error
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

