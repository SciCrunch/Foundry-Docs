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
