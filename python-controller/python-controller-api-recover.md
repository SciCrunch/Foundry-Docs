# Python Controller API - Recover

{% api-method method="post" host="https://python.scicrunch.io/controller/" path="recover" %}
{% api-method-summary %}
recover
{% endapi-method-summary %}

{% api-method-description %}
**This is an admin level API.**   
  
To be used to recover the system from **SYSTEM\_QUEUE\_FAILURE**, **SYSTEM\_ERROR** or **NETWORK\_FAILURE**. It will change the the system status to **RECOVERED**. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



