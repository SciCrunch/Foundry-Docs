---
description: Overview of the Foundry Consumer Coordinator
---

# Consumer Coordinator

### Consumer Container architecture

The consumer container coordinates a set of consumers. A consumer listens to a preconfigured message queue and applies a predefined operation to the document indicated by the received message. On success, a consumer sets the processing status of the document to a preconfigured status. Consumers are implemented as plugins with life cycle methods that are called by the consumer container during the life of the consumer in the container. The life cycle events include the creation, initialization and shutdown of a consumer. The Foundry framework provides support for two types of consumers, namely, ingestors and enhancers. The ingestors are responsible for the extraction/retrieval of data/metadata from a data source. The enhancers are responsible for transforming and enhancing the extracted source data. Each consumer runs in its own thread. The consumer container spawns only one consumer instance for each enhancer type and spawns one ingestor per data extraction source. An ingestor stays alive until all the data records from that source are extracted and terminated by the container afterwards. Enhancers are only terminated when the consumer container terminates. The consumer container is also responsible for duplicate checking and document wrapper generation.

### **Consumers/enhancers**

The consumer container subsystem of the Foundry framework manages the lifecycle of the consumers, the main units of work, of the system. Each consumer is responsible for a single atomic process applied to a data record. They are stateless and work concurrently on different data records. However, on the same record the order of operations is determined by the configured data/document processing pipeline orchestrated by the dispatcher. Consumers are implemented as plugins to a generic consumer process to simplify third party consumer development and to facilitate customizability and extensibility of the system. Transformation and data enhancement are the most common usages for consumers. Each consumer listens on a predefined message queue for messages from the dispatcher. These messages consist of the current status and the id of the data record with which the wrapper for the data record is retrieved from the MongoDB database, processed and written back before signaling the dispatcher about the current status of the document. The status messages are used by the dispatcher to determine the next consumer in the pipeline.

The types of document enhancements needed are application specific. Thus, different sets of enhancers have been developed for the projects where Foundry is used. For bioCADDIE, an NLP pipeline was developed by members of the bioCADDIE Core Development Team at the University of Texas Health Science Center at Houston for recognizing gene, disease, drug and cell line mentions in the data record metadata descriptions. This code module was converted to an enhancer using the client side plugin API. To incorporate literature citation information for data records from Protein Data Bank \(PDB\) \(18\) \(RRID:SCR\_012820\), GEO \(19\) \(RRID:SCR\_005012\) and other data sets, another enhancer was also developed that incorporates citation information from an external web service.

Since the CINERGI project is focused on enhancement of geological metadata records, time was devoted to developing an ontology-backed NLP enhancer for keyword extraction and suggestion from the metadata record, a geolocation enhancer with location named entity recognition and an organization enhancer to associate organizations in free text format in the geological metadata records with their corresponding Virtual International Authority File records.  
  


### \*\*\*\*

