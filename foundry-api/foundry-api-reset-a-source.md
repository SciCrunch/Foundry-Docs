# Foundry API: Reset a Source

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

