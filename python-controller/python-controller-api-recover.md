# Python Controller API - Recover

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="recover" method="post" summary="recover" %}
{% swagger-description %}
**This is an admin level API.**

 

\


****

\


****

To be used to recover the system from 

**SYSTEM_QUEUE_FAILURE**

, 

**SYSTEM_ERROR**

 or 

**NETWORK_FAILURE**

. It will change the the system status to 

**RECOVERED**

. 
{% endswagger-description %}

{% swagger-parameter in="header" name="api_key" type="string" %}
Authentication token 
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

