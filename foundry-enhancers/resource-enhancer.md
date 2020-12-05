# Resource Enhancer

### Resource Enhancer

**Full Path:**  
`Foundry-ES/consumers/src/main/java/org/neuinfo/foundry/consumers/jms/consumers/plugins/scicrunch/ResourceEnhancer.java`

**Synopsis:**  
By using the records' rrid, it queries Elasticsearch within the 'rrid\_mentions' index to retrieve the total count of records that have mentioned it, retrieving the count of rrid and \(rrid + resource\) mentions.

```text
"mentions" : [
    {
        "totalRRIDMentions" : {"count" : #}
        "totalMentions" : {"count" : #}
    }
]
```

**Note:** This enhancer expects the following parameters to be defined when initialized:

* `esUser` : Elasticsearch username
* `esPwd`  : Elasticsearch password
* `esURL`  : Elasticsearch URL
* `esIndexPath`: Elasticsearch path 

### Resource Enhancer Tester

**Full Path:**  
`Foundry-ES/consumers/src/test/java/org/neuinfo/foundry/consumers/ResourceMentionsEnhancerTests.java`

**Synopsis:** This class tests the correctness of the Resource Mentions Enhancer

**Note:** As stated above, be sure to include the four specified parameters when initializing the plugin

