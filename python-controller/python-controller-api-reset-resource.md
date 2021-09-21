# Python Controller API - Reset resource

{% api-method method="post" host="https://python.scicrunch.io/controller/" path="reset" %}
{% api-method-summary %}
reset
{% endapi-method-summary %}

{% api-method-description %}
This API should be run in one of the following conditions : If the source seems stuck while ingesting. OR when Foundry source\_status api shows error message "**Cannot start ingesting: Source '&lt;source name&gt;' is already ingesting/processing!"**. This is admin level API and execution is decided by the admin. It takes minimum of 2mins to maximum of 25mins to reset the source in the Foundry. This is an independent request, it is not recorded in the process\_request table of Foundry database.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="resourceID" type="string" required=true %}
Source ID to be reset
{% endapi-method-parameter %}

{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication Token
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

