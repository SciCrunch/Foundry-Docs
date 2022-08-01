# Foundry API: Source Information

{% swagger baseUrl="https://foundry-dev.scicrunch.io/foundry/api" path="/sources" method="get" summary="sources" %}
{% swagger-description %}
This endpoint allows you to get free cakes.
{% endswagger-description %}

{% swagger-parameter in="query" name="apiKey" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-response status="200" description="Response Body: (A JSON array of JSON objects one per source)." %}
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
{% endswagger-response %}

{% swagger-response status="403" description="Unauthorized request" %}
```
```
{% endswagger-response %}

{% swagger-response status="500" description="Server Error" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://foundry-dev.scicrunch.io" path="/sources/source" method="get" summary="sources/source" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="sourceID" type="string" %}
Source Identifier
{% endswagger-parameter %}

{% swagger-parameter in="query" name="dataSource" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="apiKey" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-response status="200" description="Response Body: (A JSON object)" %}
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
{% endswagger-response %}

{% swagger-response status="403" description="Unauthorized Request" %}
```
```
{% endswagger-response %}

{% swagger-response status="500" description="Server Error" %}
```
```
{% endswagger-response %}
{% endswagger %}
