# Implementing a new Enhancer

## Implementing a new Enhancer

All enhancers need to implement the `org.neuinfo.foundry.consumers.plugin.IPlugin` interface which is located in the `consumer-plugin-api` subproject of the Foundry-ES. To develop a new enhancer, you need to include the Foundry-ES `common` and `consumer-plugin-api` libraries to your Maven `pom.xml` after you have built it via `mvn -Pdev clean install` in addition to all the dependencies from `common/pom.xml` of the Foundry-ES.

```markup
<dependency>
   <groupId>org.neuinfo</groupId>
   <artifactId>foundry-es-common</artifactId>
   <version>1.0-SNAPSHOT</version>
</dependency>
<dependency>
    <groupId>org.neuinfo</groupId>
    <artifactId>foundry-es-consumer-plugin-api</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
```

The `org.neuinfo.foundry.consumers.plugin.IPlugin` interface is shown below;

```java
public interface IPlugin {

    public void setDocumentIngestionService(DocumentIngestionService dis);

    public void setGridFSService(GridFSService gridFSService);

    public void initialize(Map<String, String> options) throws Exception;

    public Result handle(DBObject docWrapper);

    public String getPluginName();

}
```

The enhancement is done in the `handle(DBObject docWrapper)` method which takes a Mongo `DBObject` object corresponding to the currently processed [document wrapper](https://github.com/SciCrunch/Foundry-Docs/tree/7fef8c44b7a5c3646af7eff39b96cbd4789ce260/developer-guide/doc_ingestion.md) from the Mongo database. If the original document is small \(less than 1MB\) it will be stored inline in the document wrapper otherwise it will be stored in the Mongo GridFS storage with a pointer in the document wrapper. Below is a code fragment to get the original document converted to JSON from the `docWrapper` regardless of where the original document is stored.

```java
BasicDBObject data = (BasicDBObject) docWrapper.get("Data");
String originalFileIDstr = (String) docWrapper.get("originalFileId");
JSONObject json;
if (!Utils.isEmpty(originalFileIDstr)) {
   // large file
   Assertion.assertNotNull(this.gridFSService);
   json = gridFSService.findJSONFile(new ObjectId(originalFileIDstr));
} else {
   DBObject originalDoc = (DBObject) docWrapper.get("OriginalDoc");
   json = JSONUtils.toJSON((BasicDBObject) originalDoc, false);
}
```

The GridFS service `org.neuinfo.foundry.common.ingestion.GridFSService` and mongo document service `org.neuinfo.foundry.common.ingestion.DocumentIngestionService` are injected to the plugin by the ES-Foundry using the setters `setGridFSService(GridFSService gridFSService)` and `setDocumentIngestionService(DocumentIngestionService dis)` methods of the IPlugin interface.

If you want to work on and update/add to the transformed data prepared by the downstream enhancers in the pipeline which is stored under `Data.transformedRec` branch of the document wrapper, you can use the following code snippet to retrieve the transformed document;

```java
BasicDBObject data = (BasicDBObject) docWrapper.get("Data");
BasicDBObject trDBO = (BasicDBObject) data.get("transformedRec");
JSONObject json = JSONUtils.toJSON(trDBO, false);
```

After you have done with enhancement, you can put back the enhanced JSON object and return the result using the following Java code snippet

```java
BasicDBObject data = (BasicDBObject) docWrapper.get("Data");
BasicDBObject trDBO = (BasicDBObject) data.get("transformedRec");
JSONObject json = JSONUtils.toJSON(trDBO, false);

// enhancement of json

data.put("transformedRec", JSONUtils.encode(json, true));
return new Result(docWrapper, Result.Status.OK_WITH_CHANGE);
```

If there is an error occurred during the enhancement you need to return an error result as shown below;

```java
Result r = new Result(docWrapper, Result.Status.ERROR);
r.setErrMessage(errorMessage);
return r;
```

