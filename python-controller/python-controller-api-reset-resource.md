# Python Controller API - Reset resource

{% swagger baseUrl="https://python.scicrunch.io/controller/" path="reset" method="post" summary="reset" %}
{% swagger-description %}
**This is an admin level API.**

 

\


****

\


****

This API should be run in one of the following conditions : If the source seems stuck while ingesting OR when Foundry source_status api shows error message "

**Cannot start ingesting: Source '<source name>' is already ingesting/processing!"**

. 

\




\


It takes minimum of 2 mins to maximum of 25 mins to reset the source in the Foundry. 

\




\




**Note:**

 This is an independent request, it is not recorded in the process_request table of Foundry database.
{% endswagger-description %}

{% swagger-parameter in="query" name="resourceID" type="string" %}
Source ID to be reset
{% endswagger-parameter %}

{% swagger-parameter in="query" name="api_key" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "message": "FINISHED"
}
```
{% endswagger-response %}
{% endswagger %}

