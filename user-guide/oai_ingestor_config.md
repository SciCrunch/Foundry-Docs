# Open Archives Initiative (OAI) Ingestor Configuration

This allows ingesting records from an [Open Archives Initiative](https://www.openarchives.org) (OAI) data source.

* **ingestURL** - The web URL to the OAI data source (e.g. `http://export.arxiv.org/oai2`).
* **sourceName** - \[String\] the name of the OAI data source (e.g. `ArXiv`) 
* **topElement** - \[String\] The top level element in a raw OAI document under which all the document \(data record\) level elements can be found. (e.g. `ListRecords`)
* **documentElement** - \[String\] the name of the field/element in the raw data under which a data record is contained. (e.g. `record`)
* **metadataPrefix** - \[String\] the name of the offset query parameter for the GET request specified by `ingestURL` for pagination.
* **allowedSetSpecs** - \[String\] the name of the limit query parameter for the GET request specified by `ingestURL` for pagination.
* **sleepTimeSecs** - \[double\] (default 1 sec)
* **sampleMode** - \["false", "true"\] Default is "false". If set to true only up to `sampleSize` data records will be ingested.
* **sampleSize** - \[int\] The number of data records that will be ingested if `sampleMode: "true"`
