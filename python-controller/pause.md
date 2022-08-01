# Python Controller API - Pause

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="pause" method="post" summary="pause" %}
{% swagger-description %}
**This is an admin level API**

\


This API is run if there is a need to pause system. For eg. 

_Code update_

 or 

_university wide network failure_

. Once run it will set the global flag to 

**PAUSED**

. If the system is PAUSED, once can not run any process except 

**`reboot, resume`**

. 

\




\




**Note:**

 Each action on this API is recorded and will update 

`process_request`

, 

`ingestors`

, 

`system_status`

 tables in the Foundry database. This request is associated with special source - 

`system_state.`

 But to run you don't need to provide this source, it is handled internally.

\




\


System pause functionality is available from client and from API.
{% endswagger-description %}

{% swagger-parameter in="path" name="api_key" type="string" %}
Authentication token
{% endswagger-parameter %}

{% swagger-response status="200" description="Cake successfully retrieved." %}
```
{
    "message": "System Paused, Controller Cannot schedule any jobs."
}
```
{% endswagger-response %}

{% swagger-response status="401" description="" %}
```
{'message' : 'Unauthorized access'}
```
{% endswagger-response %}
{% endswagger %}

From client it is run through system\_state.py script with pause argument

```
python system_state.py -h
usage: system_state.py [-h] state

positional arguments:
  state       Specify PAUSE / RESUME

optional arguments:
  -h, --help  show this help message and exit

```
