# Resource Enhancer

**Full Path:**

```text
Foundry-ES/consumers/src/main/java/org/neuinfo/foundry/consumers/jms/consumers/plugins/scicrunch/ResourceEnhancer.java
```

## Synopsis:

By using the records' rrid, it queries Elasticsearch within the 'rrid\_mentions' index to retrieve the total count of records that have mentioned it, retrieving the count of resource, rrid and total \(rrid + resource\) mentions.

**Note:** `Availability` has two values \("", "availability"\)

### **Enhancement Example**

```text
"mentions": [
	{
		"totalRRIDMentions": {
			"count": #
		},
		"totalResourceMentions": {
			"count": #
		},
		"totalMentions": {
			"count": #
		},
		"availability": {
			"keyword": ""
		},
		"timestamp": "2019-12-06 02:12:15.329"
	}
]
```

### **Enhancement Parameters**

**Note:** This enhancer expects the following parameters to be defined when initialized:

* `esUser` : Elasticsearch username
* `esPwd`  : Elasticsearch password
* `esURL`  : Elasticsearch URL
* `esIndexPath`: Elasticsearch path 

### Resource Enhancer Tester

**Full Path:**

```text
Foundry-ES/consumers/src/test/java/org/neuinfo/foundry/consumers/ResourceMentionsEnhancerTests.java
```

**Synopsis:** This class tests the correctness of the Resource Mentions Enhancer

**Note:** As stated above, be sure to include the four specified parameters when initializing the plugin

