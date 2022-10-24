# End to End Source Ingestion Tutorial (Simplified)

## Full Example of Source Ingestion

This example provides information on how to ingest a federated data resource within Foundry from scratch. This example uses sample data from [National Xenopus Resource (NXR)](https://docs.google.com/spreadsheets/d/1O2UggvZjtRRUTm1O3J8lRGeoEt8j9FGxJXxTGAiTJnI/edit?usp=sharing).

### Organism Ingestion

#### Add CSV File to Foundry Google Drive Folder

There is a Google Drive folder that contains the ingest sheets Foundry uses to ingest records:
[https://drive.google.com/drive/folders/1HuNEMHUUl8cgUoInl1EvS23dLtVWnsox?usp=sharing](https://drive.google.com/drive/folders/1HuNEMHUUl8cgUoInl1EvS23dLtVWnsox?usp=sharing)

If you do not have access to this folder you must request access.

1. Look for the sheet named **Template Ingest Sheet**. This sheet serves as a template for new _Organism_ resources that are to be added to foundry.
2. Make a copy of this template for your resource.
   - If you have already have a CSV for your resource make sure that the column names and data fields match the template sheet.
3. Make sure the name of your CSV clearly represents the resource you want to add to Foundry.
4. Name the sheet you want to ingest into foundry 'Production'.
5. In the share settings of your CSV in Google Drive make sure to change the settings so that 'Anyone with the link can view'.

#### Setup directory in Github for Source Data \(if needed\):

1. Find ID of the source at Scicrunch.org:

[https://scicrunch.org/resources/data/source/nlx_144509-1/search?q=NXR&l=NXR](https://scicrunch.org/resources/data/source/nlx_144509-1/search?q=NXR&l=NXR)

1. Get ID for source:

[https://scicrunch.org/resources/data/record/nlx_144509-1/SCR_013731/resolver?q=NXR&l=NXR&i=rrid:scr_013731](https://scicrunch.org/resources/data/record/nlx_144509-1/SCR_013731/resolver?q=NXR&l=NXR&i=rrid:scr_013731)

#### Clone Foundry Github to local machine \(if needed\):

If you already have the Foundry Github on your machine you can skip this step.

1. Navigate to the Foundry Github and click the green button that says 'Code'.
2. Copy the link under the 'ssh' option.
3. Open a new folder in your text editor of choice. Open the terminal and run the command `git clone {copiedLinkHere}`.
4. You should now have the foundry data on your local machine.

#### Create SourceDescriptor

1. Login to server using `ssh foundry` in the terminal.
2. Type the command `fd` to navigate to the _Foundry Data_ folder
3. Use the command `git pull` to pull in any new changes into Foundry.

4. In the SourceDescriptors directory create a new file for the specific source data to be ingested and transformed.
5. Please follow the file naming convention:

   `{Source ID}-{Source Resource Name}-{Resource Transformation}.yml`

SourceDescriptors/SCR_013731-NXR_Organisms_DEV-RIN.yml

7. Enter Source Information

```
SCR_013731-NXR_Organisms_DEV-RIN:
  sourceID: "SCR_013731-NXR_Organisms_DEV-RIN"
  scrID: "SCR_013731"
  name: "NXR Organisms - DEV"
  ingestMethod: "CSV"
  dataModel: "Resource Information Network"
  mappingFile: "/home/ec2-user/dev/java/Foundry-Data/Mappings/rin_prod.map"
  primaryKeyJSONPath: "$.'cat num from NXR'"
  ingestURL: "https://docs.google.com/spreadsheets/d/1O2UggvZjtRRUTm1O3J8lRGeoEt8j9FGxJXxTGAiTJnI/gviz/tq?tqx=out:csv&sheet=NXR_Live_Data"
  transformScript: "/home/ec2-user/dev/java/Foundry-Data/Transformations/SCR_013731-NXR_Organisms_DEV-RIN.trs"
  keepMissing: "false"
  ignoreLines: "1"
  headerLine: "1"
  delimiter: ","
  escapeCharacter: "&#092;"
  textQuote: "&#034;"
  qcRulesYamlFile: "/home/ec2-user/dev/java/Foundry-Data/QualityAssuranceRules/SCR_013731-NXR_Organisms_DEV-RIN.yml"
  collectionName: "SCR_013731-NXR_Organisms_DEV-RIN"
  enhancerParameters:
    "ResourceRelations": "false"
    "Semantic": "true"
    "Resource": "false"
    "Validation": "false"
```

8. File name should be unique for each resource.
9. **sourceID, scrID, name, primaryKeyJSONPath, ingestURL, transformScript, qcRulesYamlFile, collectionName** should all be unique to your resource.
10. Change the portion of the ingest url after `/d/` and before `/gviz` to the corresponding value found in your share link.

- Full link: `https://docs.google.com/spreadsheets/d/1O2UggvZjtRRUTm1O3J8lRGeoEt8j9FGxJXxTGAiTJnI/gviz/tq?tqx=out:csv&sheet=NXR_Live_Data`
- Portion to change: `1O2UggvZjtRRUTm1O3J8lRGeoEt8j9FGxJXxTGAiTJnI`

11. Make sure `sheet=NXR_Live_Data` corresponds to the name of your sheet. If you named your sheet Production it should be `sheet=Production`.

#### Commit and push your changes to Github

1. When you have created your .yml file you are ready to commit your data to the SourceDescriptors folder.
2. In your code editor use the command `git add .` in the terminal to add all of your changes to the stage.
3. In your code editor use the command `git commit -m "a message describing the work you did"` to commit your changes to the master branch.
4. In your code editor use the command `git push` to push your changes up to Github.

#### Pull your changes into Foundry

1. In your terminal run the command `ssh foundry` if you are not connected to the Foundry machine.
2. Navigate back to Foundry Data using the command `fd`.
3. Run the command `git pull` to pull your changes into the Foundry. You should see text that shows your file has been pulled into Foundry.

#### Test your config file

1. In the terminal run the command `test_config.sh SCR_013731-NXR_Organisms_DEV-RIN`.
2. The output in the terminal should return records from your CSV file with the heading names you expect. If the data does not look how you expected than you need to edit your SourceDescriptor .yml file.
3. In your code editor run `git pull` to pull the sample data to your local machine.
4. Find your resource in the sample data folder on your local machine and check to make sure the sample records look good.

#### Test the transform

1. If your sample data looks good then navigate to the "Transformations" folder in your code editor and open the auto-generated transformation script for your resource: `SCR_013731-NXR_Organisms_DEV-RIN.trs`.
2. Comment out the auto-generated transformation:
```

/*

transform column "$.'alternate_identifiers'" to "alternate_identifiers";
transform column "$.'alternative_name'" to "alternative_name";
transform column "$.'availability'" to "availability";
transform column "$.'background'" to "background";
transform column "$.'cat num from NXR'" to "cat num from NXR";
transform column "$.'catalog_id'" to "catalog_id";
transform column "$.'catalog_num_SciCrunch'" to "catalog_num_SciCrunch";
transform column "$.'database'" to "database";
transform column "$.'genomic_alteration'" to "genomic_alteration";
transform column "$.'name'" to "name";
transform column "$.'nifid'" to "nifid";
transform column "$.'notes'" to "notes";
transform column "$.'phenotype'" to "phenotype";
transform column "$.'proper_citation'" to "proper_citation";
transform column "$.'reference'" to "reference";
transform column "$.'source_constant'" to "source_constant";
transform column "$.'source_title'" to "source_title";
transform column "$.'species'" to "species";
transform column "$.'url_p'" to "url_p";

##### Not in data #####

transform column "$.'gene'" to "gene";
transform column "$.'gene_id'" to "gene_id";
transform column "$.'transgenic_insertion_type'" to "transgenic_insertion_type";

*/

```
3. Add generic transformation script:
```

/** Item Information **/
/* Set content information for record */
/* TODO: Need to decide if organsim is category or supercategory and is family then category */
let "item.types[0].name" = "organism";
let "item.types[0].curie" = "ilx:0108133";
let "item.types[0].type" = "category";
let "item.contentTypes[0].name" = "product";
let "item.contentTypes[0].curie" = "ilx:0381348";

/** Basic Information **/
/* Original source identifier */
transform column "$.'catalog_id'" to "item.identifier";

/* Normalized CURIE */
transform column "$.'proper_citation'" to "item.curie";

transform column "$.'name'" to "item.name";
transform column "$.'name'" to "item.nomenclature";

/* Construct Description */
transform column "$.'notes'" to "item.description" apply {{

description = value.replace("Description:","")
result = description.strip()

}};

/** RRID Information **/
transform column "$.'proper_citation'" to "rrid.curie";

transform column "$.'proper_citation'" to "item.docid" apply {{ result = value.lower() }};

/* Create two alternatives for now with use of proper citation */
transform column "$.'alternate_identifiers'" to "rrid.alternateRRIDs[0].curie";

let "rrid.is_unique" = "true";

/* Set some default attributes */
let "item.language" = "en";

/** Community Authority **/
transform column "$.'database'" to "authority.name";

/** Catalog Information **/
transform columns "$.'database'","$.'source_title'" to "vendors[0].name" apply {{
result = value1 + ", " + value2
}};

let "vendors[0].abbreviation" = "AGSC";
transform column "$.'catalog_id'" to "vendors[0].catalogNumber";
transform column "$.'url_p'" to "vendors[0].uri";

/** Organism Information **/
let "organisms.primary[0].role" = "primary";
transform column "$.'species'" to "organisms.primary[0].species.name";
transform column "$.'background'" to "organisms.primary[0].background.name";
let "organisms.primary[0].common.name" = "Salamander";

/* Format proper citation based on pre-formatted version */
transform column "$.'proper_citation'"  to "rrid.properCitation";


/* Phenotype information */
transform column "$.'phenotype'" to "phenotypes[].name" apply {{
arr=re.split("\s*;\s*",value,)
result=[x.strip() for x in arr]
}};

/* Notes */
transform column "$.'notes'" to "item.notes[0].description";

/* References */
transform column "$.'reference'" to "references[].curie" apply {{
arr=re.split("\s*,\s*",value,)
result=[x.strip() for x in arr]
}};

/* Gene information */
transform column "$.'gene'" to "genotype.gene[].name" apply {{
arr=re.split("\s*,\s*",value,)
result=[x.strip() for x in arr]
}};

/* Gene id information */
transform column "$.'gene_id'" to "genotype.gene[].curie" apply {{
arr=re.split("\s*;\s*",value,)
result=[x.strip() for x in arr]
}};

transform column "$.'genomic_alteration'" to "genotype.genomicAlterations[].name" apply {{
arr=re.split("\s*,|;|\|\s*",value,)
result=[x.strip() for x in arr]
}};

/* Insertion information */
transform column "$.'transgenic_insertion_type'" to "genotype.transgenicInsertion.description";

transform column "$.'availability'" to "item.availability[0].keyword";

/** Create New Style UUID **/
transform columns "$.'database'", "$.'catalog_id'" to "item.uuid" apply uuid("SCR_006372","-",value1,value2);

/** Legacy DISCO attributes **/
transform columns "$.'database'", "$.'catalog_id'" to "disco.v_uuid" apply uuid("SCR_006372","-",value1,value2);

```
4. Under "Catalog Information" heading change the abbreviation to match your stock center abbreviation. Under "Organism Information" change the organism common name to the common name of your organism. Under "Create New Style UUID" and "Legacy DISCO attributes" change the SCR RRID to the SCR RRID of your stock center.
5. In the terminal of your code editor run `git add .` and then `git commit -m "message detailing changes"`, then run `git push` to push your changes up to GitHub.
6. While connected to the foundry machine in Foundry-Data in the terminal run the command `git pull` to pull your edits into the foundry machine.

7. Then in Foundry Data run the script `test_transform.sh SCR_013731-NXR_Organisms_DEV-RIN`.
8. This will take the sample data and try to transform it, look at the output and make sure the transform output looks how you intended it to look.
9. Make sure the results of the transform look good, if there are any issues with the transform then edit your transformation script and then do steps 5 - 7 again.

#### Test QC rules

1. If the results from the transform look good then navigate to the "QualityAssuranceRules" folder in your code editor and create a new file in the directory named the same as the file you created in the "Source Descriptors" folder: `SCR_013731-NXR_Organisms_DEV-RIN.yml`.
2. If the RRIDs of your resource contain only numbers similar to **RRID:NXR_0220** then copy this information into your QC file:
```
"ValueExists":
  - path: "$.rrid.curie"
    valueRegex: "RRID:NXR_[0-9]+"
  - path: "$.disco.v_uuid"
    valueRegex: "[a-zA-Z0-9]{8}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{12}"
  - path: "$.item.uuid"
    valueRegex: "[a-zA-Z0-9]{8}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{12}"
  - path: "$.item.docid"
    valueRegex: ".+"
```
3. If the RRIDs of your resource contain both letters and number similar to **RRID:XEP_Gal047** then copy this information into your QC file instead to include lowercase and uppercase letters along with numbers in your QC check:
```
"ValueExists":
  - path: "$.rrid.curie"
    valueRegex: "RRID:XEP_[a-zA-Z0-9]+"
  - path: "$.disco.v_uuid"
    valueRegex: "[a-zA-Z0-9]{8}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{12}"
  - path: "$.item.uuid"
    valueRegex: "[a-zA-Z0-9]{8}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{4}-[a-zA-Z0-9]{12}"
  - path: "$.item.docid"
    valueRegex: ".+"
```
4. Save your changes and in the code editor in your terminal run the git commands from previous steps to push your changes up to Github.
5. Then while connected to the Foundry machine and in "Foundry-Data" run `git pull` to pull your changes into foundry. You should see your file name show up after this step.
6. Then run the script `test_qc.sh SCR_013731-NXR_Organisms_DEV-RIN` to test that your QC file is working. You should see a message 'QC rules syntax OK'.

#### Update source

1. If the QC looks good then you can run the command `update_source.sh SCR_013731-NXR_Organisms_DEV-RIN`. This will add the data to the foundry. You should see two 'BUILD SUCCESS' messages in the output.

#### Check to see your files in Foundry

1. In your terminal use the command `f` to move into 'Foundry-ES'
2. In your terminal use the command `cd bin` to move into the bin directory.
3. In your terminal use the command `./manager.sh` to open the manager.
4. In your terminal use the command `list` to see a list of resources, make sure your resource is listed. It should be at the bottom.
