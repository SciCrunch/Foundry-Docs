# Python Controller API - Clear Resource

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="clear_source" method="post" summary="clear_source" %}
{% swagger-description %}
One can not start any workflow on the source which is on HOLD. clear_source API clears the source status from HOLD to CLEAR. 
{% endswagger-description %}

{% swagger-parameter in="path" name="userID" type="integer" %}
Default auto_run (4)
{% endswagger-parameter %}

{% swagger-parameter in="path" name="resourceID" type="string" %}
Source ID to be cleared.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="api_key" type="string" %}
Authentication token to track down who is emptying our stocks.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "message": "Source is CLEAR now"
}
```
{% endswagger-response %}
{% endswagger %}

