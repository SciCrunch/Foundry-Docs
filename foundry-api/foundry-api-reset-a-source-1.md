# Foundry API: Reset a Source

{% swagger baseUrl="https://foundry-dev.scicrunch.io" path="/dashboard/reset" method="post" summary="dashboard/reset" %}
{% swagger-description %}
Resets the state of the resource in Foundry to allow further ingestion/run operations
{% endswagger-description %}

{% swagger-parameter in="body" name="apiKey" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sourceID" type="string" %}
Source Identifier
{% endswagger-parameter %}

{% swagger-response status="200" description="Reset request submitted" %}
```
{"status": "reset"}
```
{% endswagger-response %}

{% swagger-response status="400" description="If no sourceID provided or sourceID is empty" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="403" description="" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="404" description="If sourceID does not correspond to a known resource" %}
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

