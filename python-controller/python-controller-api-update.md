# Python Controller API - Update

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="update" method="post" summary="update" %}
{% swagger-description %}
This endpoint runs Update for the specified resource. Update is an integrated workflow of ingest and index.
{% endswagger-description %}

{% swagger-parameter in="query" name="jsonPath" type="string" %}
Specify the json field to be used as docID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="crawlOffset" type="integer" %}
\[1....30] Applies the date filter. Index documnets from past 'n' days.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="indexName" type="string" %}
Name of the index in Elastic Search (Controller takes care of alias mapping)
{% endswagger-parameter %}

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
Skip Accounting check (By default accounting check will be performed)
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

{% swagger-response status="400" description="Missing / Invalid resourceID" %}
```
{
    "message": "<Invalid Resource | Specify ResourceID | Failed Request : <Reason> >"
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Unauthorized Request" %}
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

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="update_status" method="get" summary="update_status" %}
{% swagger-description %}
Allows you to check the status of an ongoing update of a specific resource
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
    "status": "<Running | Finished | No ongoing update>"
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
