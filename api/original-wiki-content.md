# Original Wiki Content

## REST resources of foundry-es-man-ui

1.0-SNAPSHOT

### BASE URL: [https://foundry.scicrunch.io/foundry/api/](https://foundry.scicrunch.io/foundry/api/)

### `GET dashboard/status`

#### Request

* _Query Param_: `apiKey`, `string` 
* _Query Param_: `sourceID`, `string` 

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON object`\)

```javascript
{
  "sourceID": "SCR_013869-Cellosaurus-RIN",
  "dataSource": "SCR_013869-Cellosaurus-RIN",
  "startDate": "2019-12-17T15:53:59.000-08:00",
  "endDate": "2019-12-17T16:50:44.000-08:00",
  "ingestionEndDate": "2019-12-17T15:54:14.000-08:00",
  "new": 0,
  "resource.enhanced.1": 95,
  "ingested": 0,
  "finished": 95,
  "error": 0,
  "transformed.1": 95,
  "runStats": {
    "resourceID": "SCR_013869-Cellosaurus-RIN",
    "dataSource": "SCR_013869-Cellosaurus-RIN",
    "startDate": "Tue Dec 17 16:49:34 PST 2019",
    "endDate": "Tue Dec 17 16:50:44 PST 2019",
    "newCount": 95,
    "sameCount": 0,
    "changeCount": 5,
    "errorCount": 0,
    "finished": true,
    "opType": "partial__transform__to_end"
  }
}
```

**400 Bad Request**

**403 Forbidden**

**404 Not Found**

**500 Internal Server Error**

### `GET dashboard/status/all`

#### Request

* _Query Param_: `apiKey`, `string` 

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON array of JSON objects, one per source`\)

```javascript
[
  {
    "sourceID": "SCR_013869-Cellosaurus-RIN",
    "dataSource": "SCR_013869-Cellosaurus-RIN",
    "startDate": "2019-12-17T15:53:59.000-08:00",
    "endDate": "2019-12-17T16:50:44.000-08:00",
    "ingestionEndDate": "2019-12-17T15:54:14.000-08:00",
    "new": 0,
    "resource.enhanced.1": 95,
    "ingested": 0,
    "finished": 95,
    "error": 0,
    "transformed.1": 95,
    "runStats": {
      "resourceID": "SCR_013869-Cellosaurus-RIN",
      "dataSource": "SCR_013869-Cellosaurus-RIN",
      "startDate": "Tue Dec 17 16:49:34 PST 2019",
      "endDate": "Tue Dec 17 16:50:44 PST 2019",
      "newCount": 95,
      "sameCount": 0,
      "changeCount": 5,
      "errorCount": 0,
      "finished": true,
      "opType": "partial__transform__to_end"
    }
  },
  {
    "sourceID": "SCR_013869-Cellosaurus-RIN-test",
    "dataSource": "SCR_013869-Cellosaurus-RIN-test",
    "startDate": "2019-07-17T13:53:41.000-07:00",
    "endDate": "",
    "ingestionEndDate": "2019-07-17T13:53:43.000-07:00",
    "new": 0,
    "resource.enhanced.1": 0,
    "ingested": 10,
    "finished": 0,
    "error": 10,
    "transformed.1": 0,
    "runStats": {
      "resourceID": "SCR_013869-Cellosaurus-RIN-test",
      "dataSource": "SCR_013869-Cellosaurus-RIN-test",
      "startDate": "Wed Jul 17 13:53:41 PDT 2019",
      "newCount": 100,
      "sameCount": 90,
      "changeCount": 10,
      "errorCount": 0,
      "finished": false,
      "opType": "full"
    }
  },
  {
    "sourceID": "SCR_017612-EBRAINS_KG-KS",
    "dataSource": "SCR_017612-EBRAINS_KG-KS",
    "startDate": "2019-12-11T13:44:34.000-08:00",
    "endDate": "",
    "ingestionEndDate": "2019-12-11T13:44:38.000-08:00",
    "new": 0,
    "resource.enhanced.1": 10,
    "ingested": 26,
    "finished": 3,
    "error": 0,
    "transformed.1": 16,
    "runStats": {
      "resourceID": "SCR_017612-EBRAINS_KG-KS",
      "dataSource": "SCR_017612-EBRAINS_KG-KS",
      "startDate": "Wed Dec 11 13:44:34 PST 2019",
      "newCount": 0,
      "sameCount": 545,
      "changeCount": 26,
      "errorCount": 0,
      "finished": false,
      "opType": "full"
    }
  }
]
```

**403 Forbidden**

**500 Internal Server Error**

### `GET sources`

#### Request

* _Query Param_: `apiKey`, `string` 

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON array of JSON objects one per source`\)

```javascript
[
  {
    "sourceID": "SCR_013869-Cellosaurus-RIN-test",
    "name": "RIN - Cell Lines",
    "dataSource": "SCR_013869-Cellosaurus-RIN-test",
    "repositoryID": "",
    "transformScript": "",
    "primaryKeyJSONPath": ["$.'pr_scr_013869_1'.'e_uid'"],
    "scrID": "",
    "itemType": "",
    "dataModel": "",
    "mappingFile": "",
    "lastModified": "",
    "id": 0
  },
  {
    "sourceID": "nif-0000-00018-2",
    "name": "BAMS",
    "dataSource": "nif-0000-00018-2",
    "repositoryID": "",
    "transformScript": "<transformation-script>",
    "primaryKeyJSONPath": ["$.pr_nif_0000_00018_2.v_uuid"],
    "scrID": "",
    "itemType": "",
    "dataModel": "",
    "mappingFile": "",
    "lastModified": "",
    "id": 1
  }
]
```

**403 Forbidden**

**500 Internal Server Error**

### `GET sources/source`

#### Request

* _Query Param_: `apiKey`, `string` 
* _Query Param_: `sourceID`, `string` 
* _Query Param_: `dataSource`, `string` \(optional\) 

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON object`\)

```javascript
{
  "name": "RIN - Cell Lines",
  "sourceID": "SCR_013869-Cellosaurus-RIN",
  "dataSource": "SCR_013869-Cellosaurus-RIN",
  "repositoryID": "",
  "params": {
    "ignoreLines": "1",
    "keepMissing": "false",
    "escapeCharacter": "&#092;",
    "textQuote": "&#034;",
    "delimiter": ",",
    "useCache": "false",
    "headerLine": "1",
    "ingestURL": "file:///home/bozyurt/dev/java/Foundry-ES/test/Cell_lines_Testing.csv"
  },
  "type": "csv",
  "scrID": "",
  "itemType": "",
  "dataModel": "",
  "mappingFile": "",
  "lastModified": "Fri Dec 20 13:54:00 PST 2019"
}
```

**403 Forbidden**

**500 Internal Server Error**

### `POST dashboard/start`

ingest a resource.

#### Request

* _Form Param_: `apiKey`, `string` 
* _Form Param_: `sourceID`, `string` 

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON object`\)

```javascript
{
  "sourceID": "SCR_013869-Cellosaurus-RIN-test",
  "dataSource": "SCR_013869-Cellosaurus-RIN-test",
  "startDate": "2020-02-25T13:20:57.000-08:00",
  "endDate": "2020-02-25T13:23:04.000-08:00",
  "ingestionEndDate": "2020-02-25T13:21:14.000-08:00",
  "new": 97,
  "resource.enhanced.1": 100,
  "ingested": 100,
  "finished": 100,
  "error": 0,
  "transformed.1": 100,
  "runStats": {
    "resourceID": "SCR_013869-Cellosaurus-RIN-test",
    "dataSource": "SCR_013869-Cellosaurus-RIN-test",
    "startDate": "Tue Feb 25 13:20:57 PST 2020",
    "endDate": "Tue Feb 25 13:23:04 PST 2020",
    "newCount": 97,
    "sameCount": 0,
    "changeCount": 3,
    "errorCount": 0,
    "finished": true,
    "opType": "full"
  }
}
```

**403 Forbidden**

**500 Internal Server Error**

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

### `GET dashboard/ingest_logs`

returns all the ingestion logs for a resource in reverse chronological order.

#### Request

_No body_

* _Query Param_: `apiKey`, `string` 
* _Query Param_: `sourceID`, `string`

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON object`\)

```javascript
{"ingestLogs": [{
  "resourceID": "SCR_004712-CDC-CDIsmall",
  "dataSource": "SCR_004712-CDC-CDIsmall",
  "startDate": "Wed May 06 17:01:10 PDT 2020",
  "endDate": "Wed May 06 17:01:12 PDT 2020",
  "newCount": 14,
  "sameCount": 0,
  "changeCount": 55,
  "errorCount": 0,
  "finished": true,
  "opType": "full",
  "errorMessage": "This is only set when ingestion cannot be started"
}]}
```

**400 Bad Request**

if no sourceID is provided or sourceID is empty

**403 Forbidden**

**500 Internal Server Error**

_Response Body_: \(`error message`\)

### `POST dashboard/reset`

resets the state of a resource in Foundry to allow further ingestion/run operations.

#### Request

_No body_

* _Form Param_: `apiKey`, `string`
* _Form Param_: `sourceID`, `string`

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON object`\)

```javascript
{"status": "reset"}
```

**400 Bad Request**

if no sourceID is provided or sourceID is empty

**403 Forbidden**

**404 Not Found**

if sourceID does not correspond to a known resource

**500 Internal Server Error**

_Response Body_: \(`error message`\)

### `POST dashboard/run`

For a given resource, runs the Foundry pipeline on the records having the status specified `status2Match` starting from the pipeline step name provided with `stepName` till the end of the pipeline. This call schedules a run request to be run asynchronously and returns the request status after one second wait. Subsequent enquiries for the run status should be made via `dashboard/run_status` API call.

#### Request

_No body_

* _Form Param_: `apiKey`, `string` 
* _Form Param_: `sourceID`, `string` 
* _Form Param_: `status2Match`, `string` 
* _Form Param_: `stepName`, `string` 

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON object`\)

```javascript
{
  "status": "RUNNING",
  "logMessage": "updating status of 14 records to new.1",
  "errMessage": "<only shown if the status is ERROR>"
}
```

**400 Bad Request**

_Response Body_: \(`error message`\) if any of the sourceID, statusMatch and stepName are not provided

**403 Forbidden**

**500 Internal Server Error**

_Response Body_: \(`error message`\)

### `GET dashboard/run_status`

Returns the status of a recent run request. If no run is scheduled or the run request is already finished for the given `sourceID`, `status2Match` and `stepName`, returns HTTP `404` error.

#### Request

_No body_

* _Query Param_: `apiKey`, `string` 
* _Query Param_: `sourceID`, `string` 
* _Query Param_: `status2Match`, `string`
* _Query Param_: `stepName`, `string` 

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON Object`\)

```javascript
{
  "status": "<RUNNING|FINISHED|ERROR>",
  "logMessage": "updating status of 14 records to new.1",
  "errMessage": "<only shown if the status is ERROR>"
}
```

**400 Bad Request**

_Response Body_: \(`error message`\) if any of the sourceID, statusMatch and stepName are not provided

**403 Forbidden**

**404 Not Found**

_Response Body_: \(`error message`\) If no run is scheduled or the run request is already finished for the given `sourceID`, `status2Match` and `stepName`

**500 Internal Server Error**

_Response Body_: \(`error message`\)

### `GET dashboard/document`

Given a `documentID` returns the corresponding document wrapper as a JSON object from the MongoDB backend.

#### Request

* _Query Param_: `apiKey`, `string`
* _Query Param_: `documentID`, `string`

#### Response

_Content-Type_: `application/json`

**200 OK**

_Response Body_: \(`A JSON Object`\)

**400 Bad Request**

_Response Body_: \(`error message`\) If `documentID` is not provided.

**403 Forbidden**

**404 Not Found**

_Response Body_: \(`error message`\) If the provided `documentID` does not match any record.

**500 Internal Server Error**

_Response Body_: \(`error message`\)

