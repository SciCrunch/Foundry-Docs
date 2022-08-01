# Foundry Data Export

#### Data export

The ability to export transformed and/or enhanced data is essential for an ETL system. The exported data is used by the upstream systems. In the case of bioCADDIE, the enhanced data is indexed to an Elasticsearch endpoint used by the DataMed UI. In the case of the CINERGI project, the enhanced ISO XML metadata documents are exported as files for indexing within an ESRI Geoportal server ([https://www.esri.com/en-us/arcgis/products/geoportal-server/overview](https://www.esri.com/en-us/arcgis/products/geoportal-server/overview)). The export functionality is implemented as another enhancer/consumer in the Foundry system configured to be the final step in the processing pipeline.\
\
