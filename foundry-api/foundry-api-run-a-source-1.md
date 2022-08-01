# Foundry API: Run a Source

{% swagger baseUrl="https://foundry-dev.scicrunch.io" path="/dashboard/run" method="post" summary="dashboard/run" %}
{% swagger-description %}
For a given resource, runs the Foundry pipeline on the records having the status specified 

`status2Match`

 starting from the pipeline step name provided with 

`stepName`

 till the end of the pipeline. This call schedules a run request to be run asynchronously and returns the request status after one second wait. Subsequent enquiries for the run status should be made via 

`dashboard/run_status`

 API call.
{% endswagger-description %}

{% swagger-parameter in="body" name="apiKey" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sourceID" type="string" %}
Source Identifier
{% endswagger-parameter %}

{% swagger-parameter in="body" name="status2Match" type="string" %}
\[error | finished]
{% endswagger-parameter %}

{% swagger-parameter in="body" name="stepName" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="Response Body: (A JSON object)" %}
```
{
  "status": "RUNNING",
  "logMessage": "updating status of 14 records to new.1",
  "errMessage": "<only shown if the status is ERROR>"
}
```
{% endswagger-response %}

{% swagger-response status="400" description="If any of the sourceID, statusMatch and stepName are not provided" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="403" description="Unauthorized Request" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="500" description="Server Error" %}
```
Response Body: (error message)
```
{% endswagger-response %}
{% endswagger %}



{% swagger baseUrl="https://foundry-dev.scicrunch.io" path="/dashboard/run_status" method="get" summary="dashboard/run_status" %}
{% swagger-description %}
Returns the status of a recent run request. If no run is scheduled or the run request is already finished for the given 

`sourceID`

, 

`status2Match`

 and 

`stepName`

, returns HTTP 

`404`

 error.
{% endswagger-description %}

{% swagger-parameter in="query" name="apiKey" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="sourceID" type="string" %}
Source Identifier
{% endswagger-parameter %}

{% swagger-parameter in="query" name="status2Match" type="string" %}
\[error | finished]
{% endswagger-parameter %}

{% swagger-parameter in="query" name="stepName" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="Response Body: (A JSON Object)" %}
```
{
  "status": "<RUNNING|FINISHED|ERROR>",
  "logMessage": "updating status of 14 records to new.1",
  "errMessage": "<only shown if the status is ERROR>"
}
```
{% endswagger-response %}

{% swagger-response status="400" description="If any of the sourceID, statusMatch and stepName are not provided" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="403" description="Unauthorized Request" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="404" description="If no run is scheduled or the run request is already finished for the given sourceID, status2Match and stepName" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="500" description="" %}
```
Response Body: (error message)
```
{% endswagger-response %}
{% endswagger %}
