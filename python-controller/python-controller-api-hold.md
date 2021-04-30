# Python Controller API - Hold

{% api-method method="get" host="http://python.scicrunch.io:5000/controller/" path="hold\_source" %}
{% api-method-summary %}
hold\_source
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to put resource on HOLD
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userID" type="integer" required=false %}
Default auto\_run \(userID = 4\)
{% endapi-method-parameter %}

{% api-method-parameter name="resourceID" type="string" required=true %}
ID of the source to be put on hold
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
Authentication token to track down who is emptying our stocks.
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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



