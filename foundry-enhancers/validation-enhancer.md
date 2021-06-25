---
description: 'Alternative Name: (Bad Resource Enhancer)'
---

# Validation Enhancer

**Full Path:**

```text
Foundry-ES/consumers/src/main/java/org/neuinfo/foundry/consumers/jms/consumers/plugins/scicrunch/BadResourceEnhancer.java
```

## Synopsis:

In conjunction with the [Validation Pipeline](https://github.com/SciCrunch/Foundry-ES-Extensions/wiki/Validation-Pipeline), this enhancer inserts validation/problematic information into a record to enable the search-ability of antibodies/cell lines that have been validated, and or has shown signs of having a problematic issue.

**Note:** One should run the [Validation Pipeline](https://github.com/SciCrunch/Foundry-ES-Extensions/wiki/Validation-Pipeline) after the first iteration of re-indexing to retrieve newly ingested records.

### Enhancement Example

```text
### Antibodies ###
"validation": {
    "isValidated": true,
    "validationSites": [
        "ISCC"
    ],
    "curies": [
        "iscc"
    ],
    "totalValidationSites": {
        "count": 1
    }
},
"issues": {
    "totalIssues": {"count": 1},
    "status": ["Discontinued"],
    "direct": [{
        "issue": "Discontinued",
        "vendor": "BioLegend",
        "catalogNumber": "400618",
        "directIssue": true,
        "issueStatus": "true",
        "discontinued": true,
        "comments": "Discontinued"
    }]
}

### Cell Lines ###
'issues:'
{
  "totalIssues": {"count": 3},
  "status": [
    "Discontinued",
    "Problematic",
    "Warning"
  ],
  "global": [{
    "issue": " Contaminated",
    "comments": "Problematic cell line:  Contaminated"
  }],
  "direct": [{
    "issue": "Discontinued",
    "vendor": "KCLB",
    "catalogNumber": "90630",
    "directIssue": true,
    "issueStatus": "true",
    "discontinued": true,
    "comments": "Discontinued: KCLB; 90630; probable"
  }],
  "indirect": [{
    "issue": "Discontinued",
    "vendor": "ATCC",
    "catalogNumber": "CRL-5833",
    "directIssue": false,
    "issueStatus": "true",
    "discontinued": true,
    "comments": "Discontinued: ATCC; CRL-5833; true"
  }]
}
```



### **Tables Used for Enhancement:**

| Table Name | Description |
| :--- | :--- |
| prod\_validation\_issue\_table | Stores validation and issue information for Antibodies, Cell Lines, Etc |

### **Enhancer Parameters**

**Note:** This enhancer expects the following parameters to be defined when initialized:

* `dbURL`: The JDBC URL to the nif\_eelg database
* `dbUser`: User of the nif\_eelg database
* `dbPassword`: Password to the nif\_eelg database

**Full Path:**

```text
Foundry-ES/consumers/src/main/java/org/neuinfo/foundry/consumers/jms/consumers/plugins/scicrunch/BadResourceEnhancerTests.java
```



