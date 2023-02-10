# CSV Ingestor

* **ingestURL** - The file/web URL to the CSV file to be ingested.
* **ingestMethod:** "CSV"&#x20;
* **delimiter** - The delimiter character used to separate the CSV fields. In most cases this is comma `,`.
* **textQuote** - HTML entity code for the character used as the quote character to encapsulate, CSV fields. In most cases this is set to  `&#034;`.
* **ignoreLines** - \[int] The number of lines from the top of CSV file to be excluded. Usually this is together with `headerLine` set to `1` if CSV file has a header.
* **headerLine** - \[int] set this to `1` for CSV files with a header.
* **escapeChar** -  HTML entity code for the character used to escape quote characters occurring with the field. In most cases this is set to  `&#092;`.
* **preprocessScript** - The full path to a Bash wrapper script for the retrieval and generation of the CSV file to be ingested. The script takes a single argument for the CSV file to be saved after the retrieval/scraping etc is finished. If this is specified `ingestURL` is ignored.
* **sampleMode** - \["false", "true"] Default is "false". If set to true only up to `sampleSize` data records will be ingested.
* **sampleSize** - \[int] The number of data records that will be ingested if `sampleMode: "true"`
* **cacheMode** - \["false", "true"] Default is "false". If true uses previously retrieved data for ingestion.

## Multiple CSV File Support

Multiple CSV file support assumes that all the CSV files are a single directory and have the same format (same number and type of columns).

To ingest multiple CSV files, the `ingestURL` parameter needs to specify a local directory and a `filenamePattern` parameter is required with a Java regular expression pattern.

For example; 

```yaml
ingestURL: "file:///var/data/data-cache/SCR_001526-IMSR/data"
filenamePattern: "_file.txt$"
```
 
