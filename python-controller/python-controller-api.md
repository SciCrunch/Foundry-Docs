---
description: Describes the Controller APIs used by Foundry Dashboard to start the processes
---

# Python Controller API

{% api-method method="post" host="http" path="://foundry.controller.io:5000/ingest" %}
{% api-method-summary %}
ingest
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to start the ingest process for a foundry resource.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="-user" type="number" required=false %}
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

{% api-method-parameter name="-requestType" type="string" required=false %}
Specify the type of workflow {update, ingest, index, run, reprocess} \(default=update\)
{% endapi-method-parameter %}

{% api-method-parameter name="-sourceType" type="string" required=false %}
Specify the type of the source, {rin, literature, mentions, ks} \(default = rin\)
{% endapi-method-parameter %}

{% api-method-parameter name="-skipCheck" type="boolean" required=false %}
Skip Accounting check
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

```
{
    "message": "Your Request started"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Missing / Invalid resourceID 
{% endapi-method-response-example-description %}

```
{
    "message": "<Invalid Resource | Specify ResourceID>"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://foundry.controller.io:5000/ingest" path="\_status" %}
{% api-method-summary %}
ingest\_status
{% endapi-method-summary %}

{% api-method-description %}
Allows you to check the status of the ingest of a specific resource
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

```
{
    "status": "<Running | Finished | No ongoing ingest>"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

