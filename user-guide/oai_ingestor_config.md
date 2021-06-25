# Open Archives Initiative Protocol for Metadata Harvesting (OAI-PMH) Ingestor Configuration

This allows ingesting records from an [Open Archives Initiative](https://www.openarchives.org) (OAI) data source.

* **ingestURL** - The web URL to the OAI data source (e.g. `http://export.arxiv.org/oai2`).
* **sourceName** - \[String\] the name of the OAI data source (e.g. `ArXiv`) 
* **topElement** - \[String\] The top level element in a raw OAI document under which all the document \(data record\) level elements can be found. (e.g. `ListRecords`)
* **documentElement** - \[String\] the name of the field/element in the raw data under which a data record is contained. (e.g. `record`)
* **metadataPrefix** - \[String\]  A string to specify the metadata format in OAI-PMH requests issued to the repository (See [this](https://www.openarchives.org/OAI/openarchivesprotocol.html#metadataPrefix) for details).
* **allowedSetSpecs** - \[String\] A comma separated list of  `setSpec` (see [this](https://www.openarchives.org/OAI/openarchivesprotocol.html#Set) for details) strings. A `setSpec` is a colon [:] separated list indicating the path from the root of the set hierarchy to the respective node. A set is an optional construct for grouping items for the purpose of selective harvesting.
* **sleepTimeSecs** - \[double\] (default 1 sec) wait time between batch record requests within record set to not overwhelm the OAI-PMH server.
* **sampleMode** - \["false", "true"\] Default is "false". If set to true only up to `sampleSize` data records will be ingested.
* **sampleSize** - \[int\] The number of data records that will be ingested if `sampleMode: "true"`
* **useCache** - \["false", "true"\] If true uses previously retrieved data for ingestion.
