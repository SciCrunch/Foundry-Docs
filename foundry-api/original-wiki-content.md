# Foundry API: Document Information

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

