---
description: Overview of
---

# Foundry Ingestors / Harvesters

###  **Ingestors \(Harvesters\)**

All ingestors are implemented as plugins. The Ingestor interface has life cycle methods to initialize parameters received in the message body to start the ingestion process. These include the harvest url and ingestion type-specific parameters defined in the harvest description JSON file stored in the MongoDB under the sources collection. The startup\(\) life cycle method is generally used to get the data to an intermediate storage/cache. An ingestor plugin acts like an iterator where the hasNext\(\) method returns true if there are still more records to process and the prepPayload\(\) method returns a JSON representation of the original record harvested.

The harvesters form the extract portion of the Foundry ETL system. Both the distribution and format of the scientific data are heterogeneous. Hence, both access mode and data format need to be taken into account in devising a generic design for the harvester portion of the system. The generalizable parts, namely, the access mode of the raw data \[e.g. via FTP, RSync, web application programming interface \(API\) or a file bundle\] and distribution format \(e.g. XML, CSV or JSON\) are abstracted out. All available harvesters are parametrized to increase reusability. Another responsibility of a harvester is partitioning of the data into records to iterate over. The harvesting framework relies heavily on the iterator design pattern \(14\) similar to cursors used in relational database systems. In relational database systems, structured query language \(SQL\) queries are converted to a pipeline of relational operations on a set of cursors for the tables and indices involved in the query during the query planning phase \(15\). To support data sets that will not fit the system memory, the devised iterators are lazy and retrieve the next record on a demand basis in a streaming fashion allowing the system to process very large data files such as 0.5 TB XML file dumps from UniProt \(16\) \(RRID:SCR\_002380\). The harvester support system has iterators for the scientific data distribution formats we have encountered so far. The types of ingestors used for the bioCADDIE project are summarized in Table 1.

### Ingestors/Harvesters Used

| **Ingestor type** | **Sample source** |
| :--- | :--- |
| Web service ingestor  | Clinical Trials, Uniprot  |
| Database ingestor  | NeuroMorpho, PeptideAtlas, Clinical Trials Network  |
| OAI-PMH ingestor †  | Dryad, The Cardiovascular Research Grid  |
| Two-stage web service ingestor \*  | Inter-university Consortium for Political and Social Research, Dataverse Native  |
| Rsync ingestor  | PDB, dbGAP  |
| FTP ingestor  | BioProject, Biological Magnetic Resonance Data Bank \(BMRB\)  |
| Aspera ingestor  | GEO Datasets  |
| CSV ingestor  | Gemma  |
| XML ingestor  | ArrayExpress  |

The web service ingestor uses REST API of the source to access raw data. \*The two-stage web service ingestor also uses REST API; however, the data is accessed in two steps: first, finding the identifiers of the available data, usually through a web service providing search or summary listings, and then by retrieving each data record, through a more detailed service, by the extracted identifiers. †The Open Archives Initiative Protocol for Metadata Harvesting \(OAI-PMH\) ingestor implements OAI-PMH protocol to retrieve archived data.

**DSL for data ingestion**

For some of the data sources, an extraction step is involved, including multiple interdependent steps to access data records and/or joining multiple data file/API call results to form the data record to be extracted. To this end, we have developed a DSL for data extraction/ingestion available as a generic ingestor/harvester. Similar to the way a database management system handles the query planning and processing, the harvester language interpreter converts the declarative instructions into a set of iterators \(cursors\) that can be joined together after determining the join order.

**Ingestion DSL syntax**

The syntax of the ingestion DSL is shown in Figure 3. For all common harvesting operations such as downloading the raw data, extracting files from data distribution bundles, partitioning the data files into individual records and joining multiple raw records into a record to ingest, a DSL statement is provided. The statements in an ingestion script form a pipeline of low-level operations to prepare raw data for ingestion into the Foundry system. Statements such as ‘DOWNLOAD’ and ‘EXTRACT’ generate artifacts for the data processing statements such as PARTITION and JOIN which are identified by aliases. The aliases are used in upstream statements to identify artifacts for partitioning and combining. The script ends with an INGEST statement. From the declarative ingestion DSL script, the ingestion DSL engine creates an ingestion data preparation pipeline using the built-in cursors/iterators of the Foundry framework. The cursors can be parametrized using the SET statement as needed.

![Syntax diagram of the DSL for the retrieval/combining/ingestion of the raw scientific data.](../.gitbook/assets/image%20%2814%29.png)

An example script to extract records from the NITRC-IR data resource \(17\) \(RRID:SCR\_004162\) by joining project, subject and subject data information are shown in Figure 4.

Here, raw data is retrieved from three representational state transfer \(REST\) API calls \(the last call is parametrized\) in XML format and cached locally. Since the data retrieved contains multiple data records, they are partitioned into records via ‘partition’ statements. Each ‘row’ tag in the first two XML documents under the ‘rows’ XML tag indicate a data record. The last data set is parametrized by the subject identifier and contains only one record. It is retrieved on demand by the three-way inner join indicated by the ‘join’ statements. The fields to join on are declared as JSONPaths, since all row data formats are converted to JSON first for internal processing. The value for each parameterized REST API retrieval call comes from the value of the join data record on the left-hand side of the join. The data record to be ingested is a combination of data records from the project, project subjects and individual subject information joined by the common \(join\) fields indicated in the join statements in Figure 4.

![A sample ingestion script to retrieve and join data from three web services to form self-contained metadata records to be ingested.](../.gitbook/assets/image%20%2816%29.png)



