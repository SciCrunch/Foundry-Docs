# Python Controller API - Reboot

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="reboot" method="post" summary="reboot" %}
{% swagger-description %}
**This is an admin level API.**

\




\


This api will reboot the Primary Consumer on AWS. This is required whenever an update is pushed to Foundry. 

\




\




**Note:**

 This is an independent request, it is not recorded in the process_request table of Foundry database
{% endswagger-description %}

{% swagger-parameter in="header" name="api_key" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "message": "SUCCESS : Primary Consumer Rebooted"
}
```
{% endswagger-response %}
{% endswagger %}
