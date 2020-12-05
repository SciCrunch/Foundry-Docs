# Transformation Language Builtin Functions

Foundry transformation language is expandable with builtin functions. The following are the currently available builtin functions. Builtion functions are upto three time faster than their corresponding Python `APPLY` blocks and they should be used instead of Python `APPLY` blocks whenever it is possible.


## UUID Generator

**Input document**

    {
      "col1" : "value1",
      "col2": "value2",
      "col3": "value3",
      "col4": "value4"   
    }

**Transformation script**

    transform column "$.'col1'" to "dc.identifier" apply uuid("SCR_005400","-",value);
    transform columns "$.'col1'", "$.'col2'" to "dc.identifier2" apply uuid("SCR_005400","-",value1, value2);
    transform columns "$.'col1'", "$.'col2'", "$.'col3'" to "dc.identifier3" apply uuid("SCR_005400","-",value1, value2, value3);
    transform columns "$.'col1'", "$.'col2'", "$.'col3'", "$.'col4'"  to "dc.identifier4" apply uuid("SCR_005400","-",value1, value2, value3, value4);


**Resulting document**

    {"dc": {
      "identifier4": "7580f2d8-ed12-5812-830a-cb9351bfa486",
      "identifier": "2493dd9e-ad83-5a43-aa18-ca08d2f6e4c1",
      "identifier3": "3c6a382e-7a99-57a3-ae9b-c44abcf5f9ba",
      "identifier2": "89ea20be-2ccd-58fa-b20d-29afc6a5b972"
    }}


***
# Date Functions

**Input Document**
```json
{
    "date": "1995-02-23:23:11:08"
}
```
## toStandardDateTime

**Transformation script**
```
transform column "$.date" to "dataset.dateReleased" apply toStandardDateTime("yyyy-MM-dd:HH:mm:ss");
```

**Resulting document**
```json
{
  "dataset": {    
    "dateReleased": "19950223T231108+0000"
  }
}
```
## toStandardDate

**Transformation script**
```
transform column "$.date" to "dataset.dateReleased" apply toStandardDate("yyyy-MM-dd:HH:mm:ss");
```
**Resulting document**
```json
{
  "dataset": {
    "dateReleased": "19950223"
  }
}
```

## toStandardTime

**Transformation script**
```
transform column "$.date" to "dataset.timeReleased" apply toStandardTime("yyyy-MM-dd:HH:mm:ss");
```
**Resulting document**
```json
{
  "dataset": {
    "timeReleased": "231108+0000"
  }
}
```

## toStandardYear

**Transformation script**
```
transform column "$.date" to "dataset.yearReleased" apply toStandardYear();
```
**Resulting document**
```json
{
  "dataset": {
    "yearReleased": "1995"
  }
}
```
# concat
Concatenates two or more constant and/or variable strings to form the value of the destination field.

**Input Document**
```json
{
    "pmid": 12345678
}
```
**Transformation script**
```
transform column "$.pmid" to "dc.identifier" apply concat("pmid:",value);
```
**Resulting document**
```json
{
  "dc": {
    "identifier": "pmid:12345678"
  }
}
```
`concat` function takes arbitary number of arguments. Below is an example usage to build an RRID from id, vendor and catalog number information;

**Input Document**
```json
{
    "id": "AB_12345",
    "vendor": "ABCAM",
    "cat_num": "125"
}
```
**Transformation script**
```
transform columns "$.'id'", "$.'vendor'", "$.'cat_num'" to "rrid.properCitation" apply concat("(",value2, " Cat# ", value3,", RRID:", value1,")");
```

**Resulting document**
```json
{
  "rrid": {
    "properCitation": "(ABCAMCat#125, RRID:AB_12345)"
  }
}
```
**Python equivalent (less efficient)**
```
transform columns "$.'id'", "$.'vendor'", "$.'cat_num'" to "rrid.properCitation" apply {{ result = '(' + value2 + ' Cat# ' + value3 + ', RRID:' + value1 + ')' }};
```
# assignIfElse

This function takes four arguments; 
* the destination field value to be returned if the reference source field value is equal to the actual source field value
* the actual source field value
* the reference source field value
* the destination field value to be returned otherwise


**Input Document**
```json
{
    "majorTopic": "Y"
}
```
**Transformation script**
```
transform column "$.majorTopic" to "majorTopic" apply assignIfElse("true",value,"Y","false");
```
**Resulting document**
```json
{
  "majorTopic": "true"
}
```
***Python equivalent (less efficient)***
```
transform column "$.majorTopic" to "majorTopic" apply {{ result = 'true' if value == 'Y' else 'false' }};
```
# concatAssignIfElse

This function is similar to `assignIfElse` function above and takes 5 arguments;

* The prefix to be added to the destination field value
* the destination field value to be returned if the reference source field value is equal to the actual source field value
* the actual source field value
* the reference source field value
* the  destination field value to be returned otherwise

**Input Document**
```json
{
  "refType": "paper",
  "pmid": "12345678"
}
```
**Transformation script**
```
transform columns  "$.pmid", "$.refType"  to "curie" apply concatAssignIfElse("pmid:", value1,value2, "paper",null); 
```
**Resulting document**
```json
{
  "curie": "pmid:12345678"
}
```
***Python equivalent (less efficient)***
```
transform columns  "$.pmid", "$.refType"  to "curie" apply {{ result = 'pmid:' + value1 if value2 == 'paper' else None}};
```

# toList

This function can be used to convert a string containing a delimited list of items into a list. It takes two arguments;

* The actual source field value
* the delimeter string that separates items in the first argument value

**Input Document**
```json
{
  "supporting_agency": "NIH, NIDDK"
}
```
**Transformation script**
```
transform column "$.'supporting_agency'" to "supportingAwards[].agency.name" apply toList(value,",");
```
**Resulting document**
```json
{
  "supportingAwards": [
    {
      "agency": {
        "name": "NIH"
      }
    },
    {
      "agency": {
        "name": "NIDDK"
      }
    }
  ]
}
```
***Python equivalent (less efficient)***
```
transform column "$.'supporting_agency'" to "supportingAwards[].agency.name" apply
{{
list = re.split('\s*,\s*',value)
result = [x.strip() for x in list]
}};

```
