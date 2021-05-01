# End to End Source Ingestion Tutorial

## Full Example of Source Ingestion

This example provides information on how to ingest a federated data resource within Foundry from scratch. This example uses sample data from Data.gov - U.S. Chronic Disease Indicators \(CDI\):

[https://catalog.data.gov/dataset/u-s-chronic-disease-indicators-cdi](https://catalog.data.gov/dataset/u-s-chronic-disease-indicators-cdi)

CDC's Division of Population Health provides cross-cutting set of 124 indicators that were developed by consensus and that allows states and territories and large metropolitan areas to uniformly define, collect, and report chronic disease data that are important to public health practice and available for states, territories and large metropolitan areas. In addition to providing access to state-specific indicator data, the CDI web site serves as a gateway to additional information and data resources.

### Configure Data Source

#### Setup directory in Github for Source Data \(if needed\):

1. Find ID of source at SciCrunch.org: 

[https://scicrunch.org/scicrunch/Resources/search?q=data.gov&l=data.gov](https://scicrunch.org/scicrunch/Resources/search?q=data.gov&l=data.gov)

1. Get ID for source: 

[https://scicrunch.org/scicrunch/Resources/record/nlx\_144509-1/SCR\_004712/resolver?q=data.gov&l=data.gov](https://scicrunch.org/scicrunch/Resources/record/nlx_144509-1/SCR_004712/resolver?q=data.gov&l=data.gov)

1. Create directory in GitHub for sample data: SCR\_004712
2. Add source data files
3. Add site information and license information \(e.g. as saved webarchives in sub-directory Info-License\)

#### Create SourceDescriptor

1. In the SourceDescriptors directory create a new file for the specific source data to be ingested and transformed.  
2. Please follow the file naming convention:  

   `{Source ID}-{Source Resource Name}-{Resource Transformation}.yml`

SourceDescriptors/SCR\_004712-CDC-CDIsmall.yml

```text
3. Enter Source Information
```YAML
 SCR_004712-CDC-CDIsmall: 
  sourceID: "SCR_004712-CDC-CDIsmall" 
  name: "CDC U.S. Chronic Disease Indicators" 
  ingestMethod: "CSV" 
  primaryKeyJSONPath: "$.cell_id" 
  ingestURL: "file:///home/ec2-user/dev/java/Foundry-Data/OriginalData/SCR_004712/Tutorial/US_Chronic_Disease_Indicators_CDI_Small.csv" 
  transformScript: "/home/ec2-user/dev/java/Foundry-Data/Transformations/SCR_004712-CDC-CDIsmall.trs" 
  keepMissing: "false" 
  ignoreLines: "1" 
  headerLine: "1" 
  delimiter: "," 
  escapeCharacter: "&#092;" 
  textQuote: "&#034;"
```

1. Commit updates

#### Access Foundry

1. SSH to Foundry on AWS

   ```text
   ssh ec2-user@foundry.scicrunch.io
   ```

2. Change directory to the Foundry data directory

   ```text
   cd /home/ec2-user/dev/java/Foundry-Data
   ```

3. Get updates for Github

   ```text
   git pull
   ```

4. Change directory to the Foundry bin directory

   ```text
   cd /home/ec2-user/dev/java/Foundry-ES/bin
   ```

5. Generate Sample Transformation to test Source Ingestion. Make sure to use the source ingestion name used to create the source configuration file: _SCR\_004712-CDC-CDIsmall_

```text
./sample_transform.sh -r /home/ec2-user/dev/java/Foundry-Data/ -s SCR_004712-CDC-CDIsmall -sd /home/ec2-user/dev/java/Foundry-Data/SourceDescriptors/SCR_004712-CDC-CDIsmall.yml

 wrote /home/ec2-user/dev/java/Foundry-Data/SampleData/SCR_004712-CDC-CDIsmall/SCR_004712-CDC-CDIsmall_record_1.json
 wrote /home/ec2-user/dev/java/Foundry-Data/SampleData/SCR_004712-CDC-CDIsmall/SCR_004712-CDC-CDIsmall_record_2.json
 wrote /home/ec2-user/dev/java/Foundry-Data/SampleData/SCR_004712-CDC-CDIsmall/SCR_004712-CDC-CDIsmall_record_3.json
 wrote /home/ec2-user/dev/java/Foundry-Data/SampleData/SCR_004712-CDC-CDIsmall/SCR_004712-CDC-CDIsmall_record_4.json
 wrote /home/ec2-user/dev/java/Foundry-Data/SampleData/SCR_004712-CDC-CDIsmall/SCR_004712-CDC-CDIsmall_record_5.json
 wrote identity transformation script to file:/home/ec2-user/dev/java/Foundry-Data/Transformations/SCR_004712-CDC-CDIsmall.trs
```

1. Check sampled data files to ensure proper initial ingestion. If ingestion is not correct you will need to update the source configuration \(see section below\)

   ```text
   more /home/ec2-user/dev/java/Foundry-Data/SampleData/SCR_004712-CDC-CDIsmall/SCR_004712-CDC-CDIsmall_record_1.json
   ```

2. Change directory back to Foundry-Data to commit updates

   ```text
   cd /home/ec2-user/dev/java/Foundry-Data
   ```

3. Commit updates for sample data

   ```text
   git add /home/ec2-user/dev/java/Foundry-Data/SampleData/SCR_004712-CDC-CDIsmall
   git commit -m "Generated initial sample data"
   git push
   ```

4. Commit updates for identity transformation file

   ```text
   git add /home/ec2-user/dev/java/Foundry-Data/Transformations/SCR_004712-CDC-CDIsmall.trs
   git commit -m "Generated initial identity transformation"
   git push
   ```

#### Edit Source Configuration

If you need to edit/update the source configuration you will need to update the configuration and check updates back into GitHub and update Foundry-Data.

```text
cd /home/ec2-user/dev/java/Foundry-Data
git pull

cd /home/ec2-user/dev/java/Foundry-ES/bin
./sample_transform.sh -r /home/ec2-user/dev/java/Foundry-Data/ -s SCR_004712-CDC-CDIsmall -sd /home/ec2-user/dev/java/Foundry-Data/SourceDescriptors/SCR_004712-CDC-CDIsmall.yml

cd /home/ec2-user/dev/java/Foundry-Data
git commit -m "Updated source configuration"
git push
```

### Transforming Ingested Data

#### Customize Transformation

1. Edit the source configuration file and check into Github. You can comment out entire sections to develop transformation in phases.
2. Update files on Foundry

   ```text
   cd /home/ec2-user/dev/java/Foundry-Data
   git pull
   ```

#### Test Transformation via User Interface

1. There is a user interface that allows you to test Transformation statements.  

   ```text
   http://foundry-ui.scicrunch.io/foundry/#/transform
   API Key: 768022a9e4a37fd3d4006842ad72e159
   ```

2. Copy pieces \(or the full\) Transformation script into the UI
3. Copy one of the sample datasets \(generated above\) into the UI
4. Run the Transformation

#### Test Updated Transformation

You can test the full Transformation and workflow configuration on the server itself.

1. Go to Foundry bin directory

   ```text
   cd /home/ec2-user/dev/java/Foundry-ES/bin
   ```

2. Run Transformation and Store Resultant data in the SampleDataTransformed directory

   \`\`\`Shell

   ./transform\_checker.sh -c test -w -f /home/ec2-user/dev/java/Foundry-Data -n SCR\_004712-CDC-CDIsmall

...

## saved /home/ec2-user/dev/java/Foundry-Data/SampleDataTransformed/SCR\_004712-CDC-CDIsmall/SCR\_004712-CDC-CDIsmall\_record\_1\_tr.json

\[INFO\] ------------------------------------------------------------------------ \[INFO\] BUILD SUCCESS \[INFO\] ------------------------------------------------------------------------

```text
3. Review Sample Transformed Data
```Shell
more /home/ec2-user/dev/java/Foundry-Data/SampleDataTransformed/SCR_004712-CDC-CDIsmall/SCR_004712-CDC-CDIsmall_record_1_tr.json
```

1. Go to Foundry data directory

   ```text
   cd /home/ec2-user/dev/java/Foundry-Data
   ```

2. Add Sample Transformed Data to GitHub

   ```text
   git add /home/ec2-user/dev/java/Foundry-Data/SampleDataTransformed/SCR_004712-CDC-CDIsmall
   git commit -m "Generated initial sample transformed data"
   git push
   ```

#### Finalize Source Setup with Updated Transformation

1. Go to Foundry bin directory

   ```text
   cd /home/ec2-user/dev/java/Foundry-ES/bin
   ```

2. Generate source description for Foundry. This combines information from the source\_descriptor, source transformation, and system configuration and exports this configuration to /tmp.

   \`\`\`Shell ./source\_desc\_gen.sh -c /home/ec2-user/dev/java/Foundry-Data/SourceDescriptors/SCR\_004712-CDC-CDIsmall.yml -s SCR\_004712-CDC-CDIsmall

... wrote /tmp/SCR\_004712-CDC-CDIsmall.json

```text
3. If this completes successfully with a configuration file written to /tmp - add the source to Foundry
```Shell
./ingest_src_cli.sh -j /tmp/SCR_004712-CDC-CDIsmall.json
```

#### Update source in Foundry after edits to Transformation

1. If source ingestion has been run then remove source data from Foundry via the Manager

   \`\`\`Shell

   cd /home/ec2-user/dev/java/Foundry-ES/bin

   ./manager.sh

Foundry:&gt;&gt; list Foundry:&gt;&gt; dd SCR\_004712-CDC-CDIsmall Foundry:&gt;&gt; Ctrl-C

```text
2. Remove Source Configuration from Foundry
```Shell
./ingest_src_cli.sh -j /tmp/SCR_004712-CDC-CDIsmall.json -d
```

1. Generate Source Configuration and add Source to Foundry \(same commands as in previous section\)

   \`\`\`Shell

   ./source\_desc\_gen.sh -c /home/ec2-user/dev/java/Foundry-Data/SourceDescriptors/SCR\_004712-CDC-CDIsmall.yml -s  SCR\_004712-CDC-CDIsmall

...

> wrote /tmp/SCR\_004712-CDC-CDIsmall.json

./ingest\_src\_cli.sh -j /tmp/SCR\_004712-CDC-CDIsmall.json

```text
## Ingest Source

1. Go to Foundry bin directory
```Shell
cd /home/ec2-user/dev/java/Foundry-ES/bin
```

1. Start Manager

   ```text
   ./manager.sh
   ```

2. List Sources

   ```text
   Foundry:>> list
   ```

3. Begin Ingestion

   ```text
   Foundry:>> ingest SCR_004712-CDC-CDIsmall
   ```

4. Check Status

   ```text
   Foundry:>> status SCR_004712-CDC-CDIsmall
   ```

5. When ingestion is finished quit Manager

   ```text
   Foundry:>> Ctrl-C
   ```

### Export Data

1. Create export directory

   ```text
   mkdir /tmp/CDI
   ```

2. Go to Foundry bin directory

   ```text
   cd /home/ec2-user/dev/java/Foundry-ES/bin
   ```

3. Start Manager

   ```text
   ./manager.sh
   ```

4. List Sources

   ```text
   Foundry:>> list
   ```

5. Export transformed data

   ```text
   Foundry:>> export SCR_004712-CDC-CDIsmall finished /tmp/CDI
   ```

