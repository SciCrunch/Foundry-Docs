# Foundry API: Document Information

{% swagger baseUrl="https://foundry-dev.scicrunch.io" path="/dashboard/document" method="get" summary="dashboard/document" %}
{% swagger-description %}
Given a documentID returns the corresponding document wrapper as a JSON object from the MongoDB backend
{% endswagger-description %}

{% swagger-parameter in="query" name="apiKey" type="string" %}
Authentication Token.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="documentID" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
Response Body: (A JSON Object)
```
{% endswagger-response %}

{% swagger-response status="400" description="If documentID is not provided" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="403" description="Unauthorized Request" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="404" description="If provided documentID does not match any record" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="500" description="Server Error." %}
```
Response Body: (error message)
```
{% endswagger-response %}
{% endswagger %}

