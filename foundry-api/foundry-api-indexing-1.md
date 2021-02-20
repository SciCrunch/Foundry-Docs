# Foundry API: Indexing

{% api-method method="post" host="https://foundry-dev.scicrunch.io" path="/dashboard/index" %}
{% api-method-summary %}
dashboard/index
{% endapi-method-summary %}

{% api-method-description %}
Create ES index for a processed resource
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="apiKey" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}

{% api-method-parameter name="batchSize" type="string" required=false %}
Default is 100
{% endapi-method-parameter %}

{% api-method-parameter name="filter" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="idJsonPath" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="idList" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="mappingFile" type="string" required=false %}
Name of mapping file along with path information
{% endapi-method-parameter %}

{% api-method-parameter name="mode" type="string" required=false %}
\[full \| update\] default is full
{% endapi-method-parameter %}

{% api-method-parameter name="pkList" type="string" required=false %}
Primary key list file
{% endapi-method-parameter %}

{% api-method-parameter name="sourceID" type="string" required=true %}
Source ID to be index
{% endapi-method-parameter %}

{% api-method-parameter name="status2Match" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="urlStr" type="string" required=true %}
url string
{% endapi-method-parameter %}

{% api-method-parameter name="pwd" type="string" required=true %}
Password. \(Optional if ES server does not need authentication\)
{% endapi-method-parameter %}

{% api-method-parameter name="user" type="string" required=true %}
ES user name \(This is optional if ES server does not need authentication\)
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Indexing started. If there is an error, `numIndexed` field will not be present in the JSON response body, instead an `errMessage` field will be present.
{% endapi-method-response-example-description %}

```
{
  "url": "http://localhost:9200/scr_013869_rin_test/data",
  "status": "RUNNING",
  "numIndexed": 0,
  "errMessage": "<error message if an error has occurred>"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If any of the required parameter not provided OR provided sourceID doesn't exists
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

{% api-method method="post" host="https://foundry-dev.scicrunch.io" path="/dashboard/index\_status" %}
{% api-method-summary %}
dashboard/index\_status
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apiKey" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}

{% api-method-parameter name="urlstr" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "url": "http://localhost:9200/scr_013869_rin_test/data",
  "status": "FINISHED",
  "numIndexed": 287
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If the required parameter is malformed
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



