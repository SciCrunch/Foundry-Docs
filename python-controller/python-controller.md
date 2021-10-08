---
description: Describes various workflows supported by Python Controller
---

# Python Controller

## Python Controller Workflow

Following diagram depicts a typical workflow followed by Controller. During the process a resource is crawled / ingested and subsequently indexed to ES. At every stage logs and stats are generated and stored in the Foundry database. For any reason if the crawl ends in ERROR or resource gets STUCK the source will not be indexed and curator will be alerted via email.

![](../.gitbook/assets/image%20%283%29.png)

## Supported Workflows

Controller supports two types of workflows: Stand-Alone workflows, which can be run independently and Integrated workflows, which is combination of independent workflows.

* **Ingest \(Stand-alone Workflow\)** : Ingest the new / updated records in the source.
* **Run \(Stand-alone Workflow\)** : Reprocess the documents from Error state.

If ingest workflow ends in Error, controller internally enters into Run workflow. It executes three cycles of Run workflow. If the errors are resolved the source status changes to Finished, else it remains in Error state and Indexing gets cancelled.

![](../.gitbook/assets/image%20%2819%29.png)

* **Index \(Stand-alone Workflow\)** : Index the new / updated documents to the ES.

![](../.gitbook/assets/image%20%2820%29.png)

* **Update \(Integrated Workflow\)**: Executes the ingest followed by index workflow.
* **Reprocess \(Integrated Workflow\)** : Reprocess the documents from Finished state. Executes Run workflow from ‘finished’ state, followed by Index workflow without any filter.

## Command Line Parameters

Controller can be executed with following positional and optional parameters.

```text
  python processRequest.py

  Positional Arguments:
  resourceID            Resource name
  indexName             Index name

  Optional Arguments:
  -user USERID          userID
  -requestType          {update,index,ingest,run,reprocess}
  -sourceType           {rin,literature,mentions,ks}                        
  -f                    To Force Update
  -skipCheck            To skip accounting check
  -n                    Use mapfile to create new index
  -r                    Reset the source before ingesting
  -crawlOffset          {1,...n} Index documents from past 'n' days, [1-31]
  -stateName STATENAME  Reprocess documents from the state [error / finished]
  -jsonPath JSONPATH    Specify the Json field to be used as docID
  -errPerc ERRPERC      Specify the allowed error percentage (applicable for some resources)
  -duplPerc DUPLPERC    Specify the allowed percentage of duplicates (applicable for some resources)
```

## Request Type \(-requestType\)

Controller supports multiple request types. The default request type is update, which runs update workflow. To run any other request, it needs to be explicitly specify with this parameter.                                  `eg. -requestType=index` will run index workflow. 

## Source Type \(-sourceType\)

There are multiple source types. The default source type is rin. To ingest any other type of source, it needs to be explicitly specify with this parameter. `eg. -sourceType=literature` . If the source type is mismatched, controller will not complain. But will end up in indexing the resource under wrong source type. 

## Force Update \(-f\)

Controller will skip the prior error check for the source

## Accounting check \(-skipCheck\)

Once the ingest is finished an accounting check is performed, which calculates the percentage increase or decrease in the number of records. If there is more than 20% increase or more than 10% decrease in the records, accounting check will fail and the source will not be indexed. When ingest is run with -skipCheck parameter, Accounting check will be skipped. In case of the first ingest, accounting check is by default skipped.

## Reset source \(-r\)

**Note : This is deprecated parameter**. 

Currently the source can be reset in two ways. 

1. From client : python resetResource.py &lt;resourceID&gt;. 
2. Through reset API.

## CrawlOffset \(-crawlOffset\)

If the source needs to be indexed 'N' days after it ingested. Index process should be run with -crawlOffset parameter. It is an integer between 1-31.

## statename \(-stateName\)

One can explicitly specify the state name \(though not necessary\) from which documents will start processing. It is implemented internally. For **`run`** workflow starts from '**`error`**' state and **`reprocess`** workflow starts from '**`finished`**' state. So in a way this parameter is also deprecated

## Jsonpath \(-jsonPath\)

If you want to explicitly specify the json field to be used as a docID. eg. `-jsonPath=$.dc.identifier`

## Error Percentage \(-errPerc\)

If there are N number of errors \(even 1 error\) during ingest,  controller cancels indexing. But there are sources which needs to be updated frequently and these are known errors. In such cases you can specify **`-errPerc`** parameter, which indicates _**allowed percentage of errors for that source**_. If the number of errors are below this percentage then the curator will be notified about these errors and still index the source.

## Duplicate Percentage \(-dupPerc\)

For resources like Pubmed, Organisms  there is duplicate primary key issue. For such sources curator can specify %duplicates allowed for the resource. For eg: Per ingested count if 1% duplicates allowed then if finished record count is &gt;= that value and errorCount = 0, then the resource is clear. Controller will not report it STUCK. This resource can be indexed. This check is performed before deciding the final source status. If resource passes this dup\_param test then source status will be updated to FINISHED. Ingestion logs will be updated with relevant comment - mentioning about duplicates and controller will index the source.

