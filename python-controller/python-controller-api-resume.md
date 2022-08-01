# Python Controller API - Resume

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="resume" method="post" summary="resume" %}
{% swagger-description %}
**This is an admin level API**

\


****

\


****

It is counter method for 

`pause`

 API. To be run to resume the system, if the system is 

**PAUSED**

. It will set the global flag from 

**PAUSED**

 to 

**ALL_CLEAR**

. 

\




\




**Note**

: Each action on this API is recorded and will update process_request, ingestors and system_status tables in Foundry database.
{% endswagger-description %}

{% swagger-parameter in="path" name="api_key" type="string" %}
Authentication token
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "message": "System Resumed"
}
```
{% endswagger-response %}

{% swagger-response status="201" description="" %}
```
{
    "message": "System is not Paused, Controller can schedule jobs "
}
```
{% endswagger-response %}
{% endswagger %}

It can be run through client using system\_state.py with resume argument

```
python system_state.py -h
usage: system_state.py [-h] state

positional arguments:
  state       Specify PAUSE / RESUME

optional arguments:
  -h, --help  show this help message and exit
```

