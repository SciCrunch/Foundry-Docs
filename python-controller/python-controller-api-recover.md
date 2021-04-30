# Python Controller API - Recover

{% api-method method="get" host="http://python.scicrunch.io:5000/controller/" path="recover" %}
{% api-method-summary %}
recover
{% endapi-method-summary %}

{% api-method-description %}
To be used to recover the system from SYSTEM\_QUEUE\_FAILURE, SYSTEM\_ERROR or NETWORK\_FAILURE. It will change the the system status to RECOVERED. This api should be made by admin only.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
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



