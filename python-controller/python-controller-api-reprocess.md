# Python Controller API - Reprocess

{% api-method method="get" host="https://python.scicrunch.io/controller/" path="reprocess" %}
{% api-method-summary %}
reprocess
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to reprocess all the documents from the finished state.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userID" type="integer" required=false %}
Default auto\_run \(4\)
{% endapi-method-parameter %}

{% api-method-parameter name="index\_name" type="string" required=true %}
Name of the index \(all lowercase\)
{% endapi-method-parameter %}

{% api-method-parameter name="resourceID" type="string" required=true %}
Source ID to be reprocessed
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token 
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://python.scicrunch.io/controller/" path="reprocess\_status" %}
{% api-method-summary %}
reprocess\_status
{% endapi-method-summary %}

{% api-method-description %}
This endpoint will check the status of the reprocess workflow 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="resourceID" type="string" required=true %}
Source to be ingested
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



