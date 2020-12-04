# Foundry-ES Management \(Overview\)

## Context

Foundry-ES Management has 3 components:

* [Foundry & Foundry-API](https://github.com/SciCrunch/Foundry-ES) 
* [Foundry-Python Module](https://github.com/SciCrunch/Foundry-Python) \(**Python Controller**\)
* Foundry Dashboard 

Foundry is a message-oriented, horizontally scalable ETL system for scientific data integration and enhancement. Python Controller, interacts with Foundry through an API and automates the process of crawling / ingesting and indexing the resources. In this process a set of logs and stats are generated for every crawl and index request. These logs and stats are maintained in a MySQL database. These logs will be used by Foundry Dashboard to display the status of the resource. Python Controller is currently run as a cronjob. In future controller jobs will be scheduled from Foundry Dashboard using controller API.

![Foundry - ES Management Overview](../.gitbook/assets/image%20%282%29.png)





