---
description: 'Alternative Name: (Resource Relations Enhancer)'
---

# Relation Enhancer

**Full Path:**

```text
Foundry-ES/consumers/src/main/java/org/neuinfo/foundry/consumers/jms/consumers/plugins/scicrunch/ResourceRelationsEnhancer.java
```

## Synopsis:

By querying the`resource_relationships` table with the current record's SCR ID, the Enhancer retrieves the immediate parents and children, ancestors and descendants of the current resource.

The Enhancer recursively traverses upwards and downwards the relational tree of organizations and inserts the name and curie of these resources into the current record.

### Enhancement Example

```text
"organization" : 
{"hierarchy": {
  "parent": [{
    "name": "Digestive Disease Centers",
    "curie": "SCR_015212"
  }],
  "ancestors": [{
    "name": "Digestive Disease Centers",
    "curie": "SCR_015212"
  }],
  "children": [
    {
      "name": "CURE - Digestive Diseases Research Center Human Studies Core",
      "curie": "SCR_015207"
    },
    {
      "name": "CURE - Digestive Diseases Research Center Morphology and Imaging Core",
      "curie": "SCR_015209"
    },
    {
      "name": "CURE - Digestive Diseases Research Center Molecular Biology and Peptidomics Core",
      "curie": "SCR_015213"
    },
    {
      "name": "CURE - Digestive Diseases Research Center Animal Models Core",
      "curie": "SCR_015217"
    },
    {
      "name": "CURE - Digestive Diseases Research Center Administrative Core",
      "curie": "SCR_015231"
    }
  ],
  "descendants": [
    {
      "name": "CURE - Digestive Diseases Research Center Human Studies Core",
      "curie": "SCR_015207"
    },
    {
      "name": "CURE - Digestive Diseases Research Center Morphology and Imaging Core",
      "curie": "SCR_015209"
    },
    {
      "name": "CURE - Digestive Diseases Research Center Molecular Biology and Peptidomics Core",
      "curie": "SCR_015213"
    },
    {
      "name": "CURE - Digestive Diseases Research Center Animal Models Core",
      "curie": "SCR_015217"
    },
    {
      "name": "CURE - Digestive Diseases Research Center Administrative Core",
      "curie": "SCR_015231"
    }
  ]
}}
```

### **Tables Used for Enhancement:**

| Table Name | Description |
| :--- | :--- |
| scicrunch\_registry\_view | View containing the resources within SciCrunch |
| resource\_relationships | Contains the relationship between two sources |

### **Enhancer Parameters**

**Note:** This enhancer expects the following parameters to be defined when initialized:

* `dbURL`: The JDBC URL to the nif\_eelg database
* `dbUser`: User of the nif\_eelg database
* `dbPassword`: Password to the nif\_eelg database

### **Relation** Enhancer Tester

**Full Path:**

```text
Foundry-ES/consumers/src/test/java/org/neuinfo/foundry/consumers/ResourceRelationsEnhancerTests.java
```

