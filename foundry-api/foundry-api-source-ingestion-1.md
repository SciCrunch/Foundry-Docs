# Foundry API: Source Ingestion

{% swagger baseUrl="https://foundry-dev.scicrunch.io/foundry/api" path="/dashboard/start" method="post" summary="dashboard/start" %}
{% swagger-description %}
This endpoint allows you to ingest a resource
{% endswagger-description %}

{% swagger-parameter in="body" name="sourceID" type="string" %}
Source Identifier to be ingested
{% endswagger-parameter %}

{% swagger-parameter in="body" name="apiKey" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-response status="200" description="Response Body: (A JSON object)" %}
```
{
  "sourceID": "SCR_013869-Cellosaurus-RIN-test",
  "dataSource": "SCR_013869-Cellosaurus-RIN-test",
  "startDate": "2020-02-25T13:20:57.000-08:00",
  "endDate": "2020-02-25T13:23:04.000-08:00",
  "ingestionEndDate": "2020-02-25T13:21:14.000-08:00",
  "new": 97,
  "resource.enhanced.1": 100,
  "ingested": 100,
  "finished": 100,
  "error": 0,
  "transformed.1": 100,
  "runStats": {
    "resourceID": "SCR_013869-Cellosaurus-RIN-test",
    "dataSource": "SCR_013869-Cellosaurus-RIN-test",
    "startDate": "Tue Feb 25 13:20:57 PST 2020",
    "endDate": "Tue Feb 25 13:23:04 PST 2020",
    "newCount": 97,
    "sameCount": 0,
    "changeCount": 3,
    "errorCount": 0,
    "finished": true,
    "opType": "full"
  }
}
```
{% endswagger-response %}

{% swagger-response status="403" description=" Unauthorized request" %}
```
```
{% endswagger-response %}

{% swagger-response status="500" description="Server error" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://foundry-dev.scicrunch.io/foundry/api" path="/ingest_logs" method="get" summary="dashboard/ingest_logs" %}
{% swagger-description %}
Returns all the ingestion logs for a resource in reverse chronological order.
{% endswagger-description %}

{% swagger-parameter in="query" name="sourceID" type="string" %}
Source Identifier 
{% endswagger-parameter %}

{% swagger-parameter in="query" name="apiKey" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-response status="200" description="Response Body: (A JSON object)" %}
```
{"ingestLogs": [{
  "resourceID": "SCR_004712-CDC-CDIsmall",
  "dataSource": "SCR_004712-CDC-CDIsmall",
  "startDate": "Wed May 06 17:01:10 PDT 2020",
  "endDate": "Wed May 06 17:01:12 PDT 2020",
  "newCount": 14,
  "sameCount": 0,
  "changeCount": 55,
  "errorCount": 0,
  "finished": true,
  "opType": "full",
  "errorMessage": "This is only set when ingestion cannot be started"
}]}
```
{% endswagger-response %}

{% swagger-response status="400" description="If no sourceID is provided or sourceID is empty" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="403" description="Unauthorized Request" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="500" description="Server Error" %}
```
Response Body: (error message)
```
{% endswagger-response %}
{% endswagger %}

