## WebIngestor Configuration

* **ingestURL** - [String] The URL to retrieve data from. Acts as the argument to the `preprocessingScript` field, if it's specified.
* **parserType** - [String] ['xml' or 'json']
* **documentElement** - [String] the name of the field/element in the raw data under which a data record is contained. For XML type raw data, `documentElement` must be direct descendant of the `topElement`. For JSON type raw data, `documentElement` field can match anywhere the raw data JSON hierarchy.
* **topElement** - [String] The top level element in a raw XML document under which all the document (data record) level elements can be found. Only used for XML type remote content.
* **filterJsonPath** - [String] JSON Path to a field in a raw JSON data record. The value of matching field will be used to select data records for ingestion based on the `filterValue` configured. (Only applicable for `parserType: "json"`)
* **filterValue** - [String] The exact value or a regular expression for the raw data record field identified by the `filterJsonPath` configuration. A regular expression string needs to be prefixed by `re::` such as `filterValue: "re::^10\\.1"`.
* **useCache** - ["false", "true"] If true uses previously retrieved data for ingestion.
* **cacheFilename** - Only used if `useCache: "true"`. If specified, the filename/prefix to which the `ingestURL` contents are cached. If not specified and `useCache` is set, Foundry creates a cache file name from the `ingestURL`.
* **filenamePattern** - [String] A java regular expression to filter file names extracted from a zip file or tar ball retrieved from `ingestURL`.
* **offsetParam** - [String] the name of the offset query parameter for the GET request specified by `ingestURL` for pagination.
* **limitParam** - [String] the name of the limit query parameter for the GET request specified by `ingestURL` for pagination.
* **limitValue** - [int] the value of the the limit query parameter for the GET request specified by `ingestURL` for pagination. This specifies how many records to retrieve per page.
* **mergeIngestURLTemplate** - For list-detail type of web APIs, this field specifies the template URL with a single placeholder to retrieve the content of each data record for the list of data record ids  retrieved from the `ingestURL`. The record ids are detected using the specified `idJsonPath` and used to replace the placeholder value in the `mergeIngestURLTemplate` to create the URL to get the individual record. For example: 
```mergeIngestURLTemplate: "http://neurovault.org/api/collections/${id}/images/"```
    
* **mergeFieldName** - The JSON field for the part of the detail document record subtree that will be merged with the summary record.
* **mergeDocName** - The JSON field in the summary data record under which the subtree identified by the `mergeFieldName` in the detail record will be merged
* **idJsonPath** - [String] JSON Path to the id of the summary records retrieved by `ingestURL` for the `mergeIngestURLTemplate` placeholder.
* **normalize** - ["false", "true"] Default is "false". If set normalizes the generated JSON data record to be ingested. The normalization involves correcting array inside a single element kind of JSON generation errors.
* **preprocessScript** - The full path to a Bash wrapper script to execute web-scrapping scripts. The wrapper script takes a single argument for the data files to be saved after the retrieval/scraping etc is finished. The argument is defined via the `ingestURL` field.

> **Source Descriptor**:
> ```
> ingestURL: "file:///var/data/data-cache/SCR_010490-Protocols.io-Protocols"
> preprocessScript: "/home/ubuntu/dev/java/Foundry-Data/OriginalData/SCR_010490/wrapper.sh"
> ```

> **wrapper.sh**:
> ```
> #! /bin/bash
> python3 SCR_010490-ProtocolsIO-Ingest.py 'latest' $1
> ```


* **sampleMode** - ["false", "true"] Default is "false". If set to true only up to `sampleSize` data records will be ingested.
* **sampleSize** - [int] The number of data records that will be ingested if `sampleMode: "true"`



