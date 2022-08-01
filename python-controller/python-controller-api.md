# Python Controller API - Ingest

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="ingest" method="post" summary="ingest" %}
{% swagger-description %}
This endpoint allows you to start the ingest workflow for specified resource in Foundry.
{% endswagger-description %}

{% swagger-parameter in="query" name="userID" type="number" %}
User ID (default = 4)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="-dupPerc" type="number" %}
Allowed duplicate percentage (default = None)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="-errPerc" type="number" %}
Allowed error percentage (default = None)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="-f" type="boolean" %}
Force ingest, irrespective of prior error state (default = False)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="-sourceType" type="string" %}
Specify the type of the source, {rin, literature, mentions, ks} (default = rin)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="-skipCheck" type="boolean" %}
Skip Accounting check
{% endswagger-parameter %}

{% swagger-parameter in="query" name="resourceID" type="string" %}
Source to be ingested
{% endswagger-parameter %}

{% swagger-parameter in="query" name="api_key" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-response status="200" description="Process request started" %}
```
{
    "message": "Your Request started"
}
```
{% endswagger-response %}

{% swagger-response status="201" description="Process created but could not be completed due to following reason" %}
```
{
    "message": "Failed request - Specified resource is on HOLD. "
}
```
{% endswagger-response %}

{% swagger-response status="400" description="Missing / Invalid resourceID " %}
```
{
    "message": "<Invalid Resource | Specify ResourceID | Failed Request : <reason> >"
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Unauthorized Request" %}
```
{'message' : 'Unauthorized access'}
```
{% endswagger-response %}

{% swagger-response status="403" description="User does not have access privileges " %}
```
{'message' : 'Access Denied'}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="ingest_status" method="get" summary="ingest_status" %}
{% swagger-description %}
Allows you to check the status of an ongoing ingest of a specific resource
{% endswagger-description %}

{% swagger-parameter in="query" name="api_key" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="resourceID" type="string" %}
Source ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "status": "<Running | Finished | No ongoing ingest>"
}
```
{% endswagger-response %}

{% swagger-response status="400" description="Missing / Invalid Resource ID" %}
```
{
    "message": "<Invalid Resource | Specify ResourceID>"
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Unauthorized request" %}
```
{'message' : 'Unauthorized access'}
```
{% endswagger-response %}

{% swagger-response status="403" description="User does not have access privileges" %}
```
{'message' : 'Access Denied'}
```
{% endswagger-response %}
{% endswagger %}
