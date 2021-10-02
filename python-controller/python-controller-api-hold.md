# Python Controller API - Hold

{% api-method method="post" host="https://python.scicrunch.io/controller/" path="hold\_source" %}
{% api-method-summary %}
hold\_source
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to put resource on HOLD. Each API call will be recorded and pushed to the process\_request table of the database. One can not run any workflow on the source which is on HOLD.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="userID" type="integer" required=false %}
Default auto\_run \(userID = 4\)
{% endapi-method-parameter %}

{% api-method-parameter name="resourceID" type="string" required=true %}
ID of the source to be put on hold
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

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

This function is available through client, can be run using `on_hold.py` with `hold` argument

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

