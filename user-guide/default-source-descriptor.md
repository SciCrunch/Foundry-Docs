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
* **ingestURL:** "file:///home/ubuntu/dev/java/Foundry-Data/OriginalData/SCR\_016373/XenopusExpress.csv" \
  **Note: Option for certain ingestors**
* **transformScript:** "/home/ubuntu/dev/java/Foundry-Data/Transformations/SCR\_016373-XenopusExpress-RIN.trs"
* **primaryKeyJSONPath:** "$.'RRID\_suggested'"&#x20;
* **useCache:** "false"
* **dataModel:** "Resource Information Network"
* **mappingFile:** "/home/ubuntu/dev/java/Foundry-Data/Mappings/rin\_prod.map"
* **qcRulesYamlFile:** "/home/ubuntu/dev/java/Foundry-Data/QualityAssuranceRules/SCR\_016373-XenopusExpress-RIN.yml"
* **collectionName:** "SCR\_016373-XenopusExpress-RIN"
*   **enhancerParameters:** This parameter is optional unless a specific enhancer needs to run

    ```
    enhancerParameters:
       "ResourceRelations": "{true|false}"
       "Semantic": "{true|false}"
       "RRIDMention": "{true|false}"
       "Resource": "{true|false}"
       "Validation": "{true|false}"
    ```

    &#x20;**Note:** Enhancers are shut off by default, enhancers don't have to be explicitly set to `false`&#x20;

****
