# Python Controller API - Inactivate\_source

{% api-method method="post" host="https://python.scicrunch.io/controller/" path="inactivate\_source" %}
{% api-method-summary %}
inactivate\_source
{% endapi-method-summary %}

{% api-method-description %}
**This is an admin level API.**   
  
If a source is in **STUCK** condition and not crawled since long time \(currently there are not rules set to check\), admin can decide to flag this source as **INACTIVE**.   
  
**Note:** It is an independent API, that means using this api any source can be flagged as **INACTIVE**. Each call will be recorded and pushed to process\_request table in the database.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="resourceID" type="string" required=true %}
Source ID to be reset
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "message": "Source is INACTIVE now"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

This function is available through client, can be run using `on_hold.py` with `inactivate` argument

```text
python on_hold.py -h
usage: on_hold.py [-h] [-user USERID] [-comment COMMENT] resourceID state

positional arguments:
  resourceID        Resource name
  state             Specify HOLD / INACTIVATE

optional arguments:
  -h, --help        show this help message and exit
  -user USERID      userID
```

