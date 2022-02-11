---
description: >-
  Required Parameters for setting up a source descriptor. Refer to the specific
  ingestor docs for additional parameters to be included for ingestion.
---

# Default Source Descriptor

* **sourceID**: "SCR\_016373-XenopusExpress-RIN"&#x20;
* **name:** "Xenopus Express"&#x20;
* **scrID:** "SCR\_016373"
* **ingestMethod:** "CSV"&#x20;
* **ingestURL:** "file:///home/ubuntu/dev/java/Foundry-Data/OriginalData/SCR\_016373/XenopusExpress.csv"&#x20;
* **transformScript:** "/home/ubuntu/dev/java/Foundry-Data/Transformations/SCR\_016373-XenopusExpress-RIN.trs"
* **primaryKeyJSONPath:** "$.'RRID\_suggested'"&#x20;
* **useCache:** "false"
* **dataModel:** "Resource Information Network"
* **mappingFile:** "/home/ubuntu/dev/java/Foundry-Data/Mappings/rin\_prod.map"
* **qcRulesYamlFile:** "/home/ubuntu/dev/java/Foundry-Data/QualityAssuranceRules/SCR\_016373-XenopusExpress-RIN.yml"
* **collectionName:** "SCR\_016373-XenopusExpress-RIN"

****
