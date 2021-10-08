---
description: >-
  This endpoint runs Update for the specified sourceID. Update is an integrated
  workflow of ingest and run.
---

# Python Controller API - Update

{% api-method method="post" host="https://python.scicrunch.io/controller/" path="update" %}
{% api-method-summary %}
update
{% endapi-method-summary %}

{% api-method-description %}
This endpoint runs Update for the specified resource. Update is an integrated workflow of ingest and index.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="jsonPath" type="string" required=false %}
Specify the json field to be used as docID
{% endapi-method-parameter %}

{% api-method-parameter name="crawlOffset" type="integer" required=false %}
\[1....30\] Applies the date filter. Index documnets from past 'n' days.
{% endapi-method-parameter %}

{% api-method-parameter name="indexName" type="string" required=true %}
Name of the index in Elastic Search \(Controller takes care of alias mapping\)
{% endapi-method-parameter %}

{% api-method-parameter name="userID" type="number" required=false %}
User ID \(default = 4\)
{% endapi-method-parameter %}

{% api-method-parameter name="-dupPerc" type="number" required=false %}
Allowed duplicate percentage \(default = None\)
{% endapi-method-parameter %}

{% api-method-parameter name="-errPerc" type="number" required=false %}
Allowed error percentage \(default = None\)
{% endapi-method-parameter %}

{% api-method-parameter name="-f" type="boolean" required=false %}
Force ingest, irrespective of prior error state \(default = False\)
{% endapi-method-parameter %}

{% api-method-parameter name="-sourceType" type="string" required=false %}
Specify the type of the source, {rin, literature, mentions, ks} \(default = rin\)
{% endapi-method-parameter %}

{% api-method-parameter name="-skipCheck" type="boolean" required=false %}
Skip Accounting check \(By default accounting check will be performed\)
{% endapi-method-parameter %}

{% api-method-parameter name="resourceID" type="string" required=true %}
Source to be ingested
{% endapi-method-parameter %}

{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Process request started
{% endapi-method-response-example-description %}

```text
{
    "message": "Your Request started"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Missing / Invalid resourceID
{% endapi-method-response-example-description %}

```text
{
    "message": "<Invalid Resource | Specify ResourceID | Failed Request : <Reason> >"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Unauthorized Request
{% endapi-method-response-example-description %}

```text
{'message' : 'Unauthorized access'}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
User does not have access privileges
{% endapi-method-response-example-description %}

```text
{'message' : 'Access Denied'}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://python.scicrunch.io/controller/" path="update\_status" %}
{% api-method-summary %}
update\_status
{% endapi-method-summary %}

{% api-method-description %}
Allows you to check the status of an ongoing update of a specific resource
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}

{% api-method-parameter name="resourceID" type="string" required=true %}
Source ID
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
    "status": "<Running | Finished | No ongoing update>"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Missing / Invalid Resource ID
{% endapi-method-response-example-description %}

```text
{
    "message": "<Invalid Resource | Specify ResourceID>"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Unauthorized request
{% endapi-method-response-example-description %}

```text
{'message' : 'Unauthorized access'}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
User does not have access privileges
{% endapi-method-response-example-description %}

```text
{'message' : 'Access Denied'}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

