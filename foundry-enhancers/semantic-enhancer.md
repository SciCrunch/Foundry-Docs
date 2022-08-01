---
description: In-depth coverage of the Semantic Enhancer
---

# Semantic Enhancer

**Full Path:**

```
Foundry-ES/consumers/src/main/java/org/neuinfo/foundry/consumers/jms/consumers/plugins/scicrunch/SemanticEnhancer.java
```

## Synopsis:

Checks whether the `name`, `curie` fields are populated within the specified node. If one exists while the other doesn't, the enhancer queries the `term_mappings` table to find whether a mapping exists, otherwise it'll query the Interlex ES endpoint, retrieving the associated `name`/`curie` to create a term\_mapping.

If a match is found within the term\_mappings table and the column `curation_status` has one of the following values: \[`matched`, `approved`], matching status (`Exact Match`, `Best Mapping`) and ancestor history are inserted into the record who's `name`, `curie` fields matched the `matched_value`, `existing_id` columns respectively in the table.

### Enhancement Workflow:

![Updates records with information found in term\_mappings / Interlex](<../.gitbook/assets/Semantic Enhancer Workflow.png>)

![Semantic Enhancer Workflow (More Granular)](<../.gitbook/assets/Semantic Enhancer Workflow (1).png>)

### **Enhancement Example:**

The following provides a case where a record has the `name` field but not a `curie`. It finds the `curie` in the term\_mappings table and inserts it and additional information into the record. In this particular case, it replaces the `name` with the preferred label found in Interlex ES.

{% code title="Pre Enhancement" %}
```bash
"diseases" : 
{"related": [
  {
    "name": "Autism"
  },
  {"role": "Related Disease"}
]}
```
{% endcode %}

{% code title="Post Enhancement" %}
```bash
[2020-01-21 14:54:08,363] [INFO ] [scicrunch.SemanticEnhancer] This record searches for curie via Name
[Select4TermMappings Query]: select concept_id, curation_status from term_mappings where value = 'Autism' and view_id = 'Foundry' and view_name = 'SCR_005400-Registry-RIN' and column_name = '$.\'diseases\'.\'related\'[*]' limit 1
[Query returned the following]:
	Concept ID: ilx:0101016
	Curation Status: submitted
[2020-01-21 14:54:08,572] [INFO ] [scicrunch.SemanticEnhancer] This record is searching for a match in the term_mappings table
[2020-01-21 14:54:08,572] [INFO ] [scicrunch.SemanticEnhancer] This record inserted the following value: ilx:0101016 into the field: curie
[ES Query]: {"size":25,"query":{"bool":{"should":[{"match_phrase":{"label":"Autism"}},{"match_phrase":{"synonyms.literal":"Autism"}}]}}}
[2020-01-21 14:54:08,776] [INFO ] [scicrunch.SemanticEnhancer] Prevented Double insert
[2020-01-21 14:54:08,776] [INFO ] [scicrunch.SemanticEnhancer] Insert originalname to the following path: [diseases.related[0].originalname] | Original value: Autism
[2020-01-21 14:54:08,776] [INFO ] [scicrunch.SemanticEnhancer] This record replaced the following field: name with the value: Autistic Disorder
[2020-01-21 14:54:08,777] [INFO ] [scicrunch.SemanticEnhancer] Prevented Double insert
[2020-01-21 14:54:08,777] [INFO ] [scicrunch.SemanticEnhancer] This record inserted the following value: [{curie:"ilx:0108775",name:"Pervasive Development Disorder"}] into the field: parents
Processed Data
--------------
"diseases" : 
{"related": [
  {
    "name": "Autistic Disorder",
    "matchingStatus": "Best mapping",
    "curie": "ilx:0101016",
    "originalname": "Autism",
    "parents": [{
      "curie": "ilx:0108775",
      "name": "Pervasive Development Disorder"
    }]
  },
  {"role": "Related Disease"}
]}


```
{% endcode %}

### **Semantic Enhancer Tester**

**Full Path:**

```bash
Foundry-ES/consumers/src/test/java/org/neuinfo/foundry/consumers/SemanticEnhancerTests.java
```
