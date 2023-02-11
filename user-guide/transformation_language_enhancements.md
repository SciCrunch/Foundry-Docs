# JSON Transformation Language (JSONTL) Enhancements

## New distinct keyword

The `distinct` keyword for the `tranform column` statements allows matching of only the unique values in the source JSON document. An example usage is 
demonstrated below;


```text
transform column distinct "$.'tags'[*].'value'" to "ns.values[]";
```

**Input document**

```text
{
  "tags":[
    {"name": "name1",
     "value": "a"},
    {"name": "name1",
      "value": "b"},
    {"name": "name1",
      "value": "a"},
    {"name": "name1",
      "value": "c"},
    {"name": "name1",
      "value": "b"}
  ]
}

```
**Resulting document**

```text
{"ns": {"values": [
  "a",
  "b",
  "c"
]}}
```

## Preprocessing of source JSON records before transformation

To enforce symmetry in the source JSON documents to be tranformed, a new statement is introduced to inform whether or not normalization needs to be applied before transformation. Currently, the normalization only includes adding missing string valued fields to the arrays of JSON objects in the source data to ensure that if two or more set of fields are matched for a `transform columns` or `join` statement, corresponding fields from each JSON object in the list align. An example usage is shown below;

```text
set "normalize" on;
transform columns "$.'tags'[*].'name'","$.'tags'[*].'value'" to "ns.values[]" apply {{ result=value1 + ':' + value2 }};
```


**Input document**

```text
{
  "tags":[
    {"name": "name1",
     "value": "a"},
    {"name": "name2",
      "value": "b"},
    {"name": "name3"},
    {"name": "name4",
      "value": "c"},
    {"name": "name5",
      "value": "d"}
  ]
}

```
**Resulting document**

```text
{"ns": {"values": [
  "name1:a",
  "name2:b",
  "name3:",
  "name4:c",
  "name5:d"
]}}
```

## now function usage:

transform column "$.'id'" to "ingestTime" apply now();

```json
{"ingestTime": "2022-10-31T15:49:56.298Z"}
```

## Access to metadata in the transformation script

```
transform column "#CreationDate" to "creationDate";
transform column "#IngestTime" to "ingestTime";
```

```json
{
  "creationDate": "2022-10-31T15:54:05.939Z",
  "ingestTime": "2022-10-31T15:54:06.142Z",
}
```

Other metadata builtin variables are:

  * #CrawlDate
  * #LastSeenDate
