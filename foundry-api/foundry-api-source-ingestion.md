# Foundry API: Source Ingestion

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

\*\*\*\*

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

