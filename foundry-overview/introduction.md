---
description: >-
  An introduction to Foundry - a message-oriented, horizontally scalable ETL
  system for scientific data integration and enhancement
---

# Introduction

## A message-oriented, horizontally scalable ETL system for scientific data integration and enhancement

Modern biomedical science involves the accrual of increasingly larger data sets in many forms. SciCrunch \([https://scicrunch.org](https://scicrunch.org/)\) lists &gt;2800 databases in its resource registry, spanning biological systems from the level of genes to behavior. We know that the amount of data that is easily discoverable and accessible relative to the amount produced or that which is required to comprehensively cover a domain is limited. Therefore, calls to add to public data must also be accompanied by platforms for making these data available, searchable and useful \(FAIR, a set of guiding principles to make data Findable, Accessible, Interoperable, and Reusable\). In order to support discovery and search, there is a need to develop and deploy technologies to make the large collection of data and information resources collectively searchable.

Development of the Foundry infrastructure was informed by the following three distinct user communities the FAIR Data Informatics Lab \([RRID:SCR\_019235](https://scicrunch.org/resolver/RRID:SCR_019235)\) has been engaged with: \(i\) biomedical data set discovery \(bioCADDIE, [RRID:SCR\_004018](https://scicrunch.org/resolver/RRID:SCR_004018)\), \(ii\) biomedical information and discovery portals \(NIF, [RRID:SCR\_002894](https://scicrunch.org/resolver/RRID:SCR_002894) and dkNET, [RRID:SCR\_001606](https://scicrunch.org/resolver/RRID:SCR_001606)\) and \(iii\) Earth science resource discovery \(EarthCube Community Inventory of EarthCube Resources for Geosciences Interoperability \(CINERGI, [RRID:SCR\_002188](https://scicrunch.org/resolver/RRID:SCR_002188)\)\). The system was designed to interoperate with the current ecosystem of indices and repositories and not to replace them. The overall infrastructure consists of the following components:

* A data and metadata extraction system that is able to connect to various repositories and data aggregators/integrators using parameterized ingestors and a domain-specific language \(DSL\) to specify complex data extraction/ingestion scenarios. Incoming metadata information is converted to JavaScript Object Notation \(JSON\) for each data set being described and is stored in MongoDB.
* A loosely coupled distributed data processing pipeline management system using a message-oriented middleware \(MoM\) architecture, utilizing Apache ActiveMQ \([http://activemq.apache.org](http://activemq.apache.org/)/\), to manage the transformation and enhancement of the ingested data for data integration.
* A generic transformation language to align heterogeneous data from multiple sources with a data/metadata model \(e.g. the Data Tag Suite, DATS, [RRID:SCR\_019236](https://scicrunch.org/resolver/RRID:SCR_019236)\) enabling a broader community of curators to create and manage the transformation of data and metadata.
* Ability to develop additional processing modules that can be integrated with the overall workflow to further enhance the data and metadata records.
* Export mechanisms for the enhanced/transformed data to Elasticsearch search engine endpoints or to local file structures.





