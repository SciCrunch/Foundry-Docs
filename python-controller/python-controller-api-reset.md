# Python Controller API - Inactivate\_source

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="inactivate_source" method="post" summary="inactivate_source" %}
{% swagger-description %}
**This is an admin level API.**

 

\


****

\


****

If a source is in 

**STUCK**

 condition and not crawled since long time (currently there are not rules set to check), admin can decide to flag this source as 

**INACTIVE**

. 

\




\




**Note:**

 It is an independent API, that means using this api any source can be flagged as 

**INACTIVE**

. Each call will be recorded and pushed to process_request table in the database.
{% endswagger-description %}

{% swagger-parameter in="header" name="api_key" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="resourceID" type="string" %}
Source ID to be reset
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "message": "Source is INACTIVE now"
}
```
{% endswagger-response %}
{% endswagger %}

This function is available through client, can be run using `on_hold.py` with `inactivate` argument

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
