# Python Controller API - Run

{% api-method method="get" host="http://python.scicrunch.io:5000/controller/" path="run" %}
{% api-method-summary %}
run
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to run the source for errors.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userID" type="integer" required=false %}
If not provided default \(4- auto-run\) will be used 
{% endapi-method-parameter %}

{% api-method-parameter name="resourceID" type="string" required=true %}
Source ID to be run for errors
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token 
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```
{    "name": "Cake's name",    "recipe": "Cake's recipe name",    "cake": "Binary cake"}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find a cake matching this query.
{% endapi-method-response-example-description %}

```
{    "message": "Ain't no cake like that."}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://python.scicrunch.io:5000/controller/" path="run\_status" %}
{% api-method-summary %}
run\_status
{% endapi-method-summary %}

{% api-method-description %}
This endpoint will check the status of the ongoing run process
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userID" type="integer" required=false %}
Default auto\_run \(4\)
{% endapi-method-parameter %}

{% api-method-parameter name="resourceID" type="string" required=true %}
Source ID 
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

