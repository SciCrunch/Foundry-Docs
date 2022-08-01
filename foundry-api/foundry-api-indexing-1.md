# Foundry API: Indexing

{% swagger baseUrl="https://foundry-dev.scicrunch.io" path="/dashboard/index" method="post" summary="dashboard/index" %}
{% swagger-description %}
Create ES index for a processed resource
{% endswagger-description %}

{% swagger-parameter in="body" name="apiKey" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="batchSize" type="string" %}
Default is 100
{% endswagger-parameter %}

{% swagger-parameter in="body" name="filter" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="idJsonPath" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="idList" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="mappingFile" type="string" %}
Name of mapping file along with path information
{% endswagger-parameter %}

{% swagger-parameter in="body" name="mode" type="string" %}
\[full | update] default is full
{% endswagger-parameter %}

{% swagger-parameter in="body" name="pkList" type="string" %}
Primary key list file
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sourceID" type="string" %}
Source ID to be index
{% endswagger-parameter %}

{% swagger-parameter in="body" name="status2Match" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="urlStr" type="string" %}
url string
{% endswagger-parameter %}

{% swagger-parameter in="body" name="pwd" type="string" %}
Password. (Optional if ES server does not need authentication)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="user" type="string" %}
ES user name (This is optional if ES server does not need authentication)
{% endswagger-parameter %}

{% swagger-response status="200" description="Indexing started. If there is an error, numIndexed field will not be present in the JSON response body, instead an errMessage field will be present." %}
```
{
  "url": "http://localhost:9200/scr_013869_rin_test/data",
  "status": "RUNNING",
  "numIndexed": 0,
  "errMessage": "<error message if an error has occurred>"
}
```
{% endswagger-response %}

{% swagger-response status="400" description="If any of the required parameter not provided OR provided sourceID doesn't exists" %}
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

{% swagger baseUrl="https://foundry-dev.scicrunch.io" path="/dashboard/index_status" method="post" summary="dashboard/index_status" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="apiKey" type="string" %}
Authentication Token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="urlstr" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "url": "http://localhost:9200/scr_013869_rin_test/data",
  "status": "FINISHED",
  "numIndexed": 287
}
```
{% endswagger-response %}

{% swagger-response status="400" description="If the required parameter is malformed" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="403" description="Unauthorized Request" %}
```
Response Body: (error message)
```
{% endswagger-response %}

{% swagger-response status="404" description="" %}
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

