# Foundry API: Reset a Source

{% api-method method="post" host="https://foundry-dev.scicrunch.io" path="/dashboard/reset" %}
{% api-method-summary %}
dashboard/reset
{% endapi-method-summary %}

{% api-method-description %}
Resets the state of the resource in Foundry to allow further ingestion/run operations
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="apiKey" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}

{% api-method-parameter name="sourceID" type="string" required=true %}
Source Identifier
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Reset request submitted
{% endapi-method-response-example-description %}

```
{"status": "reset"}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If no sourceID provided or sourceID is empty
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
If sourceID does not correspond to a known resource
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



