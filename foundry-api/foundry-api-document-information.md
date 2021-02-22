# Foundry API: Document Information

{% api-method method="get" host="https://foundry-dev.scicrunch.io" path="/dashboard/document" %}
{% api-method-summary %}
dashboard/document
{% endapi-method-summary %}

{% api-method-description %}
Given a documentID returns the corresponding document wrapper as a JSON object from the MongoDB backend
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apiKey" type="string" required=true %}
Authentication Token.
{% endapi-method-parameter %}

{% api-method-parameter name="documentID" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Response Body: (A JSON Object)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If documentID is not provided
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

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
If provided documentID does not match any record
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
Server Error.
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



