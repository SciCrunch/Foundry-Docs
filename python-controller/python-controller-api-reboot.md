# Python Controller API - Reboot

{% api-method method="get" host="https://python.scicrunch.io/controller/" path="reboot" %}
{% api-method-summary %}
reboot
{% endapi-method-summary %}

{% api-method-description %}
This api will reboot the Primary Consumer on AWS. This is required whenever an update is pushed to Foundry. This is an independent request, it is not recorded in the process\_request table of Foundry database
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication Token
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

