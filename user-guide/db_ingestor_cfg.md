## DISCO Ingestor Configuration

An ingestor to ingest data from a database. This ingestor currently supports PostgreSQL and MYSQL databases.

* **jdbcURL** - [string] The Java database connectivity URL to retrieve raw data.
* **dbUser** - [string] The database user name for JDBC connection.
* **dbPassword** - [string] The database password to connect.
* **schemaName** - [string] The schema name for the database if the database has multiple schemas such as DISCO `dvp`. (optional)
* **tableName** - [string] The name of the database table to retrieve raw data.
* **tableNames** - [string] A comma separated list of database tables to be joined. Together with the parameter `joinInfo` the specified tables are joined by equi-joins to generate ingestion records. If `tableNames` is specified `tableName` should not be used.
* **joinInfo** - [string] A comma separated list of  SQL expressions of the format `<db_table1.column1> = <db_table2.colum2>` indicating pairwise equi-joins between tables specified in the `tableNames` parameter.
* **maxDocs** - [int] maximum number of records to be ingested from the database resource.
* **dbKey** - [string] The prefix for the database pre-configured in `consumers.properties` file of the Foundry. Multiple databases can be pre-configured on the Foundry system and DISCO ingestor can be configured to use one of them by providing the prefix for the needed database. In this case, you don't need to specify `jdbcURL`, `dbUser` and `dbPassword`.
* **sampleMode** - ["false", "true"] Default is "false". If set to true only up to `sampleSize` data records will be ingested.
* **sampleSize** - [int] The number of data records that will be ingested if `sampleMode: "true"`
* **filterJsonPath** - [String] JSON Path to a field in a raw JSON data record. The value of matching field will be used to select data records for ingestion based on the filterValue configured.
* **filterValue** - [String] The exact value or a regular expression for the raw data record field identified by the filterJsonPath configuration. A regular expression string needs to be prefixed by `re::` such as `filterValue: "re::^10\\.1"`.
