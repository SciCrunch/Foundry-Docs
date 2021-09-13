# Generic Quality Control Checking Utilities

Rules for checking existence of fields and specific values for fields can be defined in YAML as shown below.
Rules of different types are grouped under the rule type header. Currently there are two types of QC rules recognized: 
`ValueExists` for QC rules to check for field existence and or exact/partial match the field value gainst the the desired value. 
`CondValueExists` type QC rules are similar to `ValueExists` type QC rules where checking is done only if an additional field already exists.
The regular expressions are defined in Java regex syntax.

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

Below is a test JSON document to check against

```JSON
{
  "a1": {
    "id" : "AB1256"
  },
  "a2": {
    "id" :"CVL-2876"
  },
  "a3": {
    "id" :"2526725",
    "b": true
  }
}
```


The QC rules are specified per data source. QC rule parsing functionality can be enabled by adding a field to source descriptor 
YAML indicating the location of the YAML QC file for the data source.
An example source descriptor YAML file would like something like below
```YAML
SCR_013869-Cellosaurus-RIN:
  ...
  qcRulesYamlFile: "<full-path-to-QC-rules-YAML-file>"

```

Foundry parses the rules and caches them ready to be used inside an enhancers code. Below is an example usage:


```java
    @Override
    public Result handle(Document docWrapper) {
        try {
             Document data = (Document) docWrapper.get("Data");
             Document siDBO = (Document) docWrapper.get("SourceInfo");
             String srcId = siDBO.getString("SourceID");
             Document trDBO = (Document) data.get("transformedRec");
             JSONObject transformedJson = JSONUtils.toJSON(trDBO, false);
             
             QCRuleParserRegistry  qcRegistry = QCRuleParserRegistry.getInstance();
             QCRuleParser qcRuleParser = qcRegistry.getQCRuleParser(srcId);
             if (qcRuleParser != null) {
                 QCResult result = qcRuleParser.checkDocument(transformedJson);
                 if (result.getResult() == QCResult.Status.OK) {
                    // TODO
                 } else {
                    List<String> errors = result.getErrorMessages();
                    //TODO 
                 }
             }
             ...
        }
```
