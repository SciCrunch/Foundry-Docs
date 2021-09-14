# Python Controller API - Reset

{% api-method method="post" host="https://python.scicrunch.io/controller/" path="reset" %}
{% api-method-summary %}
reset
{% endapi-method-summary %}

{% api-method-description %}
This api call will reset the specified resource in the foundry. It takes minimum 2mins to maximum of 25mins to reset the resource. It depends on the size of the resource.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="resourceID" type="string" required=true %}
Source ID to be reset
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

