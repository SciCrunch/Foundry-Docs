# Python Controller

## Python Controller Workflow

Following diagram depicts a typical workflow followed by Controller. During the process a resource is crawled / ingested and subsequently indexed to ES. At every stage logs and stats are generated and stored in the Foundry database. For any reason if the crawl ends in ERROR or resource gets STUCK the source will not be indexed and curator will be alerted via email.

![](../.gitbook/assets/image%20%283%29.png)

## Supported Workflows

Controller supports two types of workflows: Stand-Alone workflows, which can be run independently and Integrated workflows, which is combination of independent workflows.

* **Ingest \(Stand-alone Workflow\)** : Ingest the new / updated records in the source
* **Run \(Stand-alone Workflow\)** : Reprocess the documents from Error state. ![Ingest - Run Workflow](https://github.com/SciCrunch/Foundry-Python/blob/master/images/Foundry%20-%20Ingest-Run%20workflow.jpeg)
* **Index \(Stand-alone Workflow\)** : Index the new / updated documents to the ES ![Index Workflow](https://github.com/SciCrunch/Foundry-Python/blob/master/images/Foundry%20-%20Index%20workflow.jpeg)
* **Update \(Integrated Workflow\)**: Executes the ingest followed by index workflow
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

## Force Update \(-f\)

Controller will skip the prior error check for the source

## Accounting check \(-skipCheck\)

Once the ingest is finished an accounting check is performed, which calculates the percentage increase or decrease in the number of records. If there is more than 20% increase or more than 10% decrease in the records, accounting check will fail and the source will not be indexed. When ingest is run with -skipCheck parameter, Accounting check will be skipped. In case of the first ingest accounting check is by default skipped.

