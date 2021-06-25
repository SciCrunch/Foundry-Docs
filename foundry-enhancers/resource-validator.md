---
description: 'Alternative Name: (Quality Assurance Enhancer)'
---

# Resource Validator

**Full Path:**

```text
Foundry-ES/consumers/src/main/java/org/neuinfo/foundry/consumers/jms/consumers/plugins/scicrunch/QualityAssuranceEnhancer.java
```

## Synopsis:

Currently checking RIN sources, this Enhancer performs a number of checks to confirm the validity of the current record.

Checks the record if a RRID, v\_uuid exists, otherwise it flags the records as `error` and prints out the record information and error to the logs.

**Full Path:**

```text
Foundry-ES/consumers/src/main/java/org/neuinfo/foundry/consumers/jms/consumers/plugins/scicrunch/QualityAssuranceEnhancerTests.java
```



