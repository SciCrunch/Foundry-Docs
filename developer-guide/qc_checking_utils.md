# Generic Quality Control Checking Utilities

Rules for checking existence of fields and specific values for fields can be defined in YAML as shown below.
Rules of different types are grouped under the rule type header. Currently there are two types of QC rules recognized: 
`ValueExists` for QC rules to check for field existence and or exact/partial match the field value gainst the the desired value. 


```yaml
"ValueExists":
  - path: "$.a1.id"
    valueRegex: "AB.+"
  - path: "$.a2.id"
    value: "CVL-2876"
  - path: "$.a3.id"
"CondValueExists":
  - condPath: "$.a3.b"
    path: "$.a3.id"
    valueRegex: "\\d+"
```
