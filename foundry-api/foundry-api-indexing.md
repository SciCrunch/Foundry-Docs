# Foundry API: Indexing \(old\)

### `POST dashboard/index`

create ES index for a processed resource

#### Request

* _Form Param_: `apiKey`, `string` 
* _Form Param_: `batchSize`, `integer`  \(optional default:100\)
* _Form Param_: `filter`, `string` \(optional\)
* _Form Param_: `idJsonPath`, `string`  \(optional\)
* _Form Param_: `idList`, `string` \(optional\)
* _Form Param_: `mappingFile`, `string`  \(optional\)
* _Form Param_: `mode`, `string` \(optional \[full\|update\] default:full\)
* _Form Param_: `pkList`, `string` \(optional primary key list file\)
* _Form Param_: `pwd`, `string`  \(optional if ES server does not need authentication\)
* _Form Param_: `sourceID`, `string` 
* _Form Param_: `status2Match`, `string` 
* _Form Param_: `urlStr`, `string` 
* _Form Param_: `user`, `string` \(optional if ES server does not need authentication\)

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON object`\)

```javascript
{
  "url": "http://localhost:9200/scr_013869_rin_test/data",
  "status": "RUNNING",
  "numIndexed": 0,
  "errMessage": "<error message if an error has occurred>"
}
```

If there is an error, `numIndexed` field will not be present in the JSON response body, instead an `errMessage` field will be present.

**400 Bad Request**

_Response Body_: \(`error message`\)

**403 Forbidden**

**500 Internal Server Error**

_Response Body_: \(`error message`\)

### `GET dashboard/index_status`

#### Request

* _Query Param_: `apiKey`, `string` 
* _Query Param_: `urlStr`, `string` 

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON object`\)

```javascript
{
  "url": "http://localhost:9200/scr_013869_rin_test/data",
  "status": "FINISHED",
  "numIndexed": 287
}
```

**400 Bad Request**

_Response Body_: \(`error message`\)

**403 Forbidden**

**404 Not Found**

_Response Body_: \(`error message`\)

**500 Internal Server Error**

_Response Body_: \(`error message`\)

