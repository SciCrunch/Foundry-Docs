---
description: Information on providing LinkOut information via Foundry
---

# NCBI LinkOut

## Foundry Linkout

### [What Linkout is](https://www.ncbi.nlm.nih.gov/projects/linkout/)

LinkOut is a service that allows you to link directly from PubMed and other NCBI databases to a wide range of information and services beyond the NCBI systems. LinkOut aims to facilitate access to relevant online resources in order to extend, clarify, and supplement information found in NCBI databases. Examples of LinkOut Resources include full-text publications, biological databases, consumer health information, research tools, and more.

**For Additional Information about the linkout process:** [https://www.ncbi.nlm.nih.gov/projects/linkout/doc/publinkout.html](https://www.ncbi.nlm.nih.gov/projects/linkout/doc/publinkout.html)

### Linkout Preparation

#### File Preparation: Identity File

The identity file contains the information needed to list a provider in LinkOut. This file must be named providerinfo.xml; the file name is case sensitive. The file should be composed in a text editor, such as NotePad, not in a word processing program.

The following is an example providerinfo.xml file for the LinkOut participant, Good Publisher, Inc. with Provider Id 8888 and NameAbbr GoodPublisher.

```text
<?xml version="1.0"?>
<!DOCTYPE Provider PUBLIC "-//NLM//DTD LinkOut 1.0//EN"
"https://www.ncbi.nlm.nih.gov/projects/linkout/doc/LinkOut.dtd">
<Provider>
<!-- ProviderId is assigned by NCBI -->
    <ProviderId>8888</ProviderId>
    <Name>Good Publisher, Inc.</Name>
    <NameAbbr>GoodPublisher</NameAbbr>
    <SubjectType>publishers/providers</SubjectType>
    <Attribute>subscription/membership/fee required</Attribute>
<!-- Url is used in My NCBI and the LinkOut Journals and Providers lists -->
    <Url>http://www.goodpublisher.com</Url>
<!-- Brief is used in My NCBI -->
    <Brief>
    An international publisher of biomedical journals and books
    </Brief>
</Provider>
```

`<SubjectType> and <Attribute>` elements included in the providerinfo.xml file will apply to all links submitted by the provider. In the example above, a subscription is required to access all full text at the provider’s site, therefore subscription/membership/fee required has been included in the providerinfo.xml file.

#### File Preparation: Resource CSV File

Links data can also be provided in CSV \(comma separated values\) files. The CSV resource file contains LinkOut data provider identifiers, PubMed citation Ids or queries, and links data from your journal site, all of which is used to create links in PubMed.

A LinkOut program converts CSV files in to XML files that validate against the LinkOut DTD. Links provided in CSV files must link directly from a PubMed citation to the corresponding article full text.

CSV files need to have the file extension .csv; the file extension is case sensitive. File names may contain alpha-numeric characters and underscores only. Special characters and spaces are not allowed. Examples of file name and extension: journaltitle\_2vol.csv, or freearticles\_Feb2015.csv, or fulltext\_2\_15.csv. To help with file management, a provider may submit more than one resource file. CSV files may not exceed 10 MB each.

**Resource CSV File Data Fields**

The CSV files used by LinkOut to create links in PubMed have required and optional data fields:

Field 1: PrId \(required\). Provider Id assigned by NCBI to links data providers. A four-digit number.

Field 2: DB \(required\). NCBI database name. Enter PubMed in this field.

Field 3: UID or Query \(required\). Each record in an NCBI database has a numerical unique identifier \(UID\). The unique identifier for PubMed citations is the citation PMID. For example, in this citation: [https://www.ncbi.nlm.nih.gov/pubmed/24255994](https://www.ncbi.nlm.nih.gov/pubmed/24255994) the summary display lists the PubMed citation Id \(PMID\) below the article citation:

Genetic screening for PRA-associated mutations in multiple dog breeds shows that PRA is heterogeneous within and between breeds.

Downs LM, Hitti R, Pregnolato S, Mellersh CS.

Vet Ophthalmol. 2014 Mar;17\(2\):126-30. doi: 10.1111/vop.12122. Epub 2013 Nov 21.

**PMID:24255994**

Each PubMed record can also be retrieved using a query. For example, the above citation would be retrieved in PubMed using this query: “Vet Ophthalmol”\[ta\] AND 17\[vol\] AND 126\[pg\]

Field 4: URL \(required\). The URL to the article full text for a PubMed citation.

Filed 5: IconUrl \(optional\). URL of an icon file that you would like to represent your journal. The icon should meet the specifications described in Icons. The icon URL should point directly to the icon file in your server. If an icon is not provided, LinkOut will use the LinkOut generic icon.

Field 6: UrlName\(optional\). Additional description about the article link.

Field 7: SubjectType \(required_\). SubjectType is used to determine where links will be placed in the “LinkOut – more resources” display. In this field enter the subject type ‘publishers/providers.’ \(_\) If the ‘publishers/providers’ subject type is present in the identity file, this field should be left empty.

Field 8: Attribute \(required\). Enter “subscription/membership/fee required.” If the article full text is either free or open access enter either ‘Full-text online’ for the full text in HTML, or ‘Full-text PDF’ for the full text in PDF. Note that for article full text that requires a subscription, the attribute “Full-text online” or “Full-text PDF” must be listed in the identity file.

**Resource File CSV Format**

Your CSV file can be formatted as a table. Each field must be separated by commas. The CSV file format to create links in PubMed that lead to the article full text is the following:

Field 1: PrId. Provider Id, a four-digit number. For example: 1234.

Field 2: DB. Enter ‘PubMed’ in this field.

Field 3: Two options UID or Query:

UID. PubMed citation Id \(PMID\). For example: 11532607

Query. A query that leads to the PubMed record for an article: “Front Biosci”\[ta\] AND 6\[vol\] AND D1128\[pg\]

Field 4: URL. [https://www.bioscience.org/2001/v6/d/highland/fulltext.htm](https://www.bioscience.org/2001/v6/d/highland/fulltext.htm)

Filed 5: IconUrl. [https://www.bioscience.org/images/medlink.jpg](https://www.bioscience.org/images/medlink.jpg)

Field 6: UrlName. Review article

Field 7: SubjectType. Publishers/providers \(\*\) If the ‘publishers/providers’ subject type is present in the identity file, this field should be left empty.

Field 8: Attribute. Subscription/membership/fee required. Note that because the article full text is only available through subscription, the attribute “Full-text online” or “Full-text PDF” must be listed in the identity file. If this article were to be available free or open access, Field 8 would need to have either the attribute “Full-text online” or “Full-text PDF.”

When access to journal articles is available at the journal site in a combination of free, subscription only, or selected open access, provide separate CSV files for each. For example, links data to free articles would be provided separately from links data that is available through subscription only. Note that different icons can be provided for each type of link to display clearly in PubMed whether the article full text is available through subscription only, free, or open access.

**Example:**

```text
Field 1: PrId. 1234

Field 2: DB. PubMed

Field 3: UID. 11282572 and 11532607

Field 4: URL. https://www.bioscience.org/2001/v6/a/torshin/fulltext.htm and https://www.bioscience.org/2001/v6/d/highland/fulltext.htm

Filed 5: IconUrl. https://www.bioscience.org/images/medlink.jpg

Field 6: UrlName None and Review

Field 7: SubjectType. None (already present in the identity file)

Field 8: Attribute. Subscription/membership/fee required
```

### Linkout Through Foundry

A Python script will be developed to generate source specific exports.  It will need to be determined where this configuration information is stored.  Perhaps a YAML file in a LinkOut directory withing Foundry-Data. This script will pull data from the resource's respective ES index, formats the data into the appropriate format expected from NCBI, and transfers the files to NCBI's server.

