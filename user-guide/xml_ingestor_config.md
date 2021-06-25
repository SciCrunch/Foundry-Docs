# XML Ingestor Configuration

* **ingestURL** - The file/web URL to the XML file to be ingested.
* **topElement** - The delimiter character used to separate the CSV fields. In most cases this is comma `,`.
* **documentElement** - HTML entity code for the character used as the quote character to encapsulate, CSV fields. In most cases this is set to  `&#034;`.
* **offsetParam** - \[int\] The number of lines from the top of CSV file to be excluded. Usually this is together with `headerLine` set to `1` if CSV file has a header.
* **limitParam** - \[int\] set this to `1` for CSV files with a header.
* **sampleMode** - \["false", "true"\] Default is "false". If set to true only up to `sampleSize` data records will be ingested.
* **sampleSize** - \[int\] The number of data records that will be ingested if `sampleMode: "true"`
* **cacheMode** - \["false", "true"\] Default is "false". If true uses previously retrieved data for ingestion.
