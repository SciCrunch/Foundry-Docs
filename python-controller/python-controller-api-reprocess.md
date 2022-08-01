# Python Controller API - Reprocess

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="reprocess" method="post" summary="reprocess" %}
{% swagger-description %}
This endpoint allows you to reprocess all the documents from the finished state.
{% endswagger-description %}

{% swagger-parameter in="path" name="userID" type="integer" %}
Default auto_run (4)
{% endswagger-parameter %}

{% swagger-parameter in="path" name="index_name" type="string" %}
Name of the index (all lowercase)
{% endswagger-parameter %}

{% swagger-parameter in="path" name="resourceID" type="string" %}
Source ID to be reprocessed
{% endswagger-parameter %}

{% swagger-parameter in="header" name="api_key" type="string" %}
Authentication token 
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

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="reprocess_status" method="post" summary="reprocess_status" %}
{% swagger-description %}
This endpoint will check the status of the reprocess workflow 
{% endswagger-description %}

{% swagger-parameter in="query" name="resourceID" type="string" %}
Source to be ingested
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

