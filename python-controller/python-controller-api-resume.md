# Python Controller API - Resume

{% api-method method="post" host="https://python.scicrunch.io/controller/" path="resume" %}
{% api-method-summary %}
resume
{% endapi-method-summary %}

{% api-method-description %}
**This is an admin level API**  
  
It is counter method for `pause` API. To be run to resume the system, if the system is **PAUSED**. It will set the global flag from **PAUSED** to **ALL\_CLEAR**. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "message": "System Resumed"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "message": "System is not Paused, Controller can schedule jobs "
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

It can be run through client using system\_state.py with resume argument

```text
python system_state.py -h
usage: system_state.py [-h] state

positional arguments:
  state       Specify PAUSE / RESUME

optional arguments:
  -h, --help  show this help message and exit
```



