---
description: Describes the APIs for checking the source's status
---

# Foundry API: Status Information

{% api-method method="get" host="https://foundry-dev.scicrunch.io" path="/foundry/api/dashboard/status" %}
{% api-method-summary %}
dashboard/status
{% endapi-method-summary %}

{% api-method-description %}
Gives the status of a single source
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apiKey" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}

{% api-method-parameter name="sourceID" type="string" required=true %}
Source to be ingested
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "sourceID": "SCR_013869-Cellosaurus-RIN",
  "dataSource": "SCR_013869-Cellosaurus-RIN",
  "startDate": "2019-12-17T15:53:59.000-08:00",
  "endDate": "2019-12-17T16:50:44.000-08:00",
  "ingestionEndDate": "2019-12-17T15:54:14.000-08:00",
  "new": 0,
  "resource.enhanced.1": 95,
  "ingested": 0,
  "finished": 95,
  "error": 0,
  "transformed.1": 95,
  "runStats": {
    "resourceID": "SCR_013869-Cellosaurus-RIN",
    "dataSource": "SCR_013869-Cellosaurus-RIN",
    "startDate": "Tue Dec 17 16:49:34 PST 2019",
    "endDate": "Tue Dec 17 16:50:44 PST 2019",
    "newCount": 95,
    "sameCount": 0,
    "changeCount": 5,
    "errorCount": 0,
    "finished": true,
    "opType": "partial__transform__to_end"
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://foundry-dev.scicrunch.io/foundry/api/dashboard/status/all " path="" %}
{% api-method-summary %}
dashboard/status/all
{% endapi-method-summary %}

{% api-method-description %}
Gives the status of all the sources
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
A JSON array of JSON objects, one per source
{% endapi-method-response-example-description %}

```
[
  {
    "sourceID": "SCR_013869-Cellosaurus-RIN",
    "dataSource": "SCR_013869-Cellosaurus-RIN",
    "startDate": "2019-12-17T15:53:59.000-08:00",
    "endDate": "2019-12-17T16:50:44.000-08:00",
    "ingestionEndDate": "2019-12-17T15:54:14.000-08:00",
    "new": 0,
    "resource.enhanced.1": 95,
    "ingested": 0,
    "finished": 95,
    "error": 0,
    "transformed.1": 95,
    "runStats": {
      "resourceID": "SCR_013869-Cellosaurus-RIN",
      "dataSource": "SCR_013869-Cellosaurus-RIN",
      "startDate": "Tue Dec 17 16:49:34 PST 2019",
      "endDate": "Tue Dec 17 16:50:44 PST 2019",
      "newCount": 95,
      "sameCount": 0,
      "changeCount": 5,
      "errorCount": 0,
      "finished": true,
      "opType": "partial__transform__to_end"
    }
  },
  {
    "sourceID": "SCR_013869-Cellosaurus-RIN-test",
    "dataSource": "SCR_013869-Cellosaurus-RIN-test",
    "startDate": "2019-07-17T13:53:41.000-07:00",
    "endDate": "",
    "ingestionEndDate": "2019-07-17T13:53:43.000-07:00",
    "new": 0,
    "resource.enhanced.1": 0,
    "ingested": 10,
    "finished": 0,
    "error": 10,
    "transformed.1": 0,
    "runStats": {
      "resourceID": "SCR_013869-Cellosaurus-RIN-test",
      "dataSource": "SCR_013869-Cellosaurus-RIN-test",
      "startDate": "Wed Jul 17 13:53:41 PDT 2019",
      "newCount": 100,
      "sameCount": 90,
      "changeCount": 10,
      "errorCount": 0,
      "finished": false,
      "opType": "full"
    }
  },
  {
    "sourceID": "SCR_017612-EBRAINS_KG-KS",
    "dataSource": "SCR_017612-EBRAINS_KG-KS",
    "startDate": "2019-12-11T13:44:34.000-08:00",
    "endDate": "",
    "ingestionEndDate": "2019-12-11T13:44:38.000-08:00",
    "new": 0,
    "resource.enhanced.1": 10,
    "ingested": 26,
    "finished": 3,
    "error": 0,
    "transformed.1": 16,
    "runStats": {
      "resourceID": "SCR_017612-EBRAINS_KG-KS",
      "dataSource": "SCR_017612-EBRAINS_KG-KS",
      "startDate": "Wed Dec 11 13:44:34 PST 2019",
      "newCount": 0,
      "sameCount": 545,
      "changeCount": 26,
      "errorCount": 0,
      "finished": false,
      "opType": "full"
    }
  }
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



