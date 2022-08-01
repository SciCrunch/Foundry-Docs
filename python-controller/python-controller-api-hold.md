# Python Controller API - Hold

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="hold_source" method="post" summary="hold_source" %}
{% swagger-description %}
This endpoint allows you to put resource on HOLD. Each API call will be recorded and pushed to the process_request table of the database. One can not run any workflow on the source which is on HOLD.
{% endswagger-description %}

{% swagger-parameter in="path" name="userID" type="integer" %}
Default auto_run (userID = 4)
{% endswagger-parameter %}

{% swagger-parameter in="path" name="resourceID" type="string" %}
ID of the source to be put on hold
{% endswagger-parameter %}

{% swagger-parameter in="header" name="api_key" type="string" %}
Authentication token 
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "message": "Source is on HOLD"
}
```
{% endswagger-response %}
{% endswagger %}

This function is available through client, can be run using `on_hold.py` with `hold` argument

```
python on_hold.py -h
usage: on_hold.py [-h] [-user USERID] [-comment COMMENT] resourceID state

positional arguments:
  resourceID        Resource name
  state             Specify HOLD / INACTIVATE

optional arguments:
  -h, --help        show this help message and exit
  -user USERID      userID

```
