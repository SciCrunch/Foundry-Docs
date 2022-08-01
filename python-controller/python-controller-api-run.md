# Python Controller API - Run

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="run" method="post" summary="run" %}
{% swagger-description %}
This endpoint allows you to run the source for errors.
{% endswagger-description %}

{% swagger-parameter in="query" name="api_key" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="resourceID" type="string" %}
Source ID to be run for errors
{% endswagger-parameter %}

{% swagger-parameter in="query" name="userID" type="integer" %}
If not provided default (4 - auto-run) will be used
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "message": "Your Request started"
}
```
{% endswagger-response %}

{% swagger-response status="400" description="" %}
```
{
    "message": "<Invalid Resource | Specify ResourceID | Failed Request : <Reason> >"
}
```
{% endswagger-response %}

{% swagger-response status="401" description="" %}
```
{'message' : 'Unauthorized access'}
```
{% endswagger-response %}

{% swagger-response status="403" description="" %}
```
{'message' : 'Access Denied'}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="run_status" method="get" summary="run_status" %}
{% swagger-description %}
This endpoint will check the status of the ongoing run process
{% endswagger-description %}

{% swagger-parameter in="query" name="api_key" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="resourceID" type="string" %}
Source ID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="userID" type="integer" %}
Default auto_run (4)
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}
