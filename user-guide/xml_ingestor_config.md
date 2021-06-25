# XML Ingestor Configuration

To ingest results in XML format from a web service with optional pagination.

* **ingestURL** - The web URL to the XML file to be ingested.
* **documentElement** - \[String\] the name of the field/element in the raw data under which a data record is contained. The `documentElement` must be direct descendant of the `topElement`.
* **topElement** - \[String\] The top level element in a raw XML document under which all the document \(data record\) level elements can be found.
* **offsetParam** - \[String\] the name of the offset query parameter for the GET request specified by `ingestURL` for pagination.
* **limitParam** - \[String\] the name of the limit query parameter for the GET request specified by `ingestURL` for pagination.
* **limitValue** - \[int\] the value of the the limit query parameter for the GET request specified by `ingestURL` for pagination. This specifies how many records to retrieve per page.
* **sampleMode** - \["false", "true"\] Default is "false". If set to true only up to `sampleSize` data records will be ingested.
* **sampleSize** - \[int\] The number of data records that will be ingested if `sampleMode: "true"`
