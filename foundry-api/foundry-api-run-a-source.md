# Foundry API: Run a Source

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

