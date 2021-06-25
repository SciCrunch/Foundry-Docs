# XML Ingestor Configuration

* **ingestURL** - The file/web URL to the XML file to be ingested.
* **documentElement** - \[String\] the name of the field/element in the raw data under which a data record is contained. The `documentElement` must be direct descendant of the `topElement`.
* **topElement** - \[String\] The top level element in a raw XML document under which all the document \(data record\) level elements can be found.
* **offsetParam** - \[int\] The number of lines from the top of CSV file to be excluded. Usually this is together with `headerLine` set to `1` if CSV file has a header.
* **limitParam** - \[int\] set this to `1` for CSV files with a header.
* **sampleMode** - \["false", "true"\] Default is "false". If set to true only up to `sampleSize` data records will be ingested.
* **sampleSize** - \[int\] The number of data records that will be ingested if `sampleMode: "true"`
* **cacheMode** - \["false", "true"\] Default is "false". If true uses previously retrieved data for ingestion.
