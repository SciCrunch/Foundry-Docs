# Foundry API: Source Information \(old\)

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

