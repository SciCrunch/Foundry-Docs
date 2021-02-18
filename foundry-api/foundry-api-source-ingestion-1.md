# Foundry API: Source Ingestion

{% api-method method="post" host="https://foundry-dev.scicrunch.io/foundry/api" path="/dashboard/start" %}
{% api-method-summary %}
dashboard/start
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to ingest a resource
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="sourceID" type="string" required=true %}
Source Identifier to be ingested
{% endapi-method-parameter %}

{% api-method-parameter name="apiKey" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
_Response Body_: \(`A JSON object`\)
{% endapi-method-response-example-description %}

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
Server error
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://foundry-dev.scicrunch.io/foundry/api" path="/ingest\_logs" %}
{% api-method-summary %}
dashboard/ingest\_logs
{% endapi-method-summary %}

{% api-method-description %}
Returns all the ingestion logs for a resource in reverse chronological order.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="sourceID" type="string" required=true %}
Source Identifier 
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
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If no sourceID is provided or sourceID is empty
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Unauthorized Request
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
Server Error
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



