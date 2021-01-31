# FTP Ingestor

* **ftpHost** - \[String\] The FTP host URL to retrieve data from.
* **remotePath** - \[String\] The remote directory path for the raw data on the FTP site.
* **parserType** - \[String\] \['xml' or 'json'\] \(default 'xml'\)
* **filenamePattern** - \[String\] A java regular expression to match file names to be retrieved from the `remotePath` of the FTP site specified by `ftpHost`.
* **recursive** - \["false", "true"\] If true all the directories under the `remotePath` is scanned recursively to find matching raw data.
* **outDir** - \[String\] full path to a local directory under which the matching FTP files will be downloaded. 
* **documentElement** - \[String\] the name of the field/element in the raw data under which a data record is contained. For XML type raw data, `documentElement` must be direct descendant of the `topElement`. For JSON type raw data, `documentElement` field can match anywhere the raw data JSON hierarchy.
* **topElement** - \[String\] The top level element in a raw XML document under which all the document \(data record\) level elements can be found. Only used for XML type remote content.
* **largeRecords** - \["false", true\] Default is "false". If set to true the raw data records are persisted by the Mongo GridFS instead of being embedded directly into the document wrapper Mongo document. This option is used only for datasets where each record is larger than 20 MB.
* **maxDocs** - \[int\] Maximum number of records to ingest from the FTP site \(optional\).
* **sampleMode** - \["false", "true"\] Default is "false". If set to true only up to `sampleSize` data records will be ingested. \(optional\)
* **sampleSize** - \[int\] The number of data records that will be ingested if `sampleMode: "true"` \(optional\).

