# Foundry API: Run a Source

{% api-method method="post" host="https://foundry-dev.scicrunch.io" path="/dashboard/run" %}
{% api-method-summary %}
dashboard/run
{% endapi-method-summary %}

{% api-method-description %}
For a given resource, runs the Foundry pipeline on the records having the status specified `status2Match` starting from the pipeline step name provided with `stepName` till the end of the pipeline. This call schedules a run request to be run asynchronously and returns the request status after one second wait. Subsequent enquiries for the run status should be made via `dashboard/run_status` API call.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="apiKey" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}

{% api-method-parameter name="sourceID" type="string" required=true %}
Source Identifier
{% endapi-method-parameter %}

{% api-method-parameter name="status2Match" type="string" required=true %}
\[error \| finished\]
{% endapi-method-parameter %}

{% api-method-parameter name="stepName" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
_Response Body_: \(`A JSON object`\)
{% endapi-method-response-example-description %}

```
{
  "status": "RUNNING",
  "logMessage": "updating status of 14 records to new.1",
  "errMessage": "<only shown if the status is ERROR>"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If any of the sourceID, statusMatch and stepName are not provided
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Unauthorized Request
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
Server Error
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



{% api-method method="get" host="https://foundry-dev.scicrunch.io" path="/dashboard/run\_status" %}
{% api-method-summary %}
dashboard/run\_status
{% endapi-method-summary %}

{% api-method-description %}
Returns the status of a recent run request. If no run is scheduled or the run request is already finished for the given `sourceID`, `status2Match` and `stepName`, returns HTTP `404` error.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apiKey" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}

{% api-method-parameter name="sourceID" type="string" required=true %}
Source Identifier
{% endapi-method-parameter %}

{% api-method-parameter name="status2Match" type="string" required=true %}
\[error \| finished\]
{% endapi-method-parameter %}

{% api-method-parameter name="stepName" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
_Response Body_: \(`A JSON Object`\)
{% endapi-method-response-example-description %}

```
{
  "status": "<RUNNING|FINISHED|ERROR>",
  "logMessage": "updating status of 14 records to new.1",
  "errMessage": "<only shown if the status is ERROR>"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If any of the sourceID, statusMatch and stepName are not provided
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Unauthorized Request
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
If no run is scheduled or the run request is already finished for the given `sourceID`, `status2Match` and `stepName`
{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Response Body: (error message)
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

