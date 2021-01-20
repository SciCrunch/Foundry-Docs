# Debugging Hints

## **Only 1 record has been ingested \(no errors in ingest\)**

It's most likely the case that the specified column for `primaryKeyJSONPath` \(located within the resource's YML file\) doesn't have unique values to act as a primary key. 

  
**Solution**: Use another column or combine multiple columns to achieve unique values

## **The number of ingested records doesn't match the number of input records \(no errors in ingest\)**

This is most likely due to records with the same primary key. It's most likely the case that the specified column for `primaryKeyJSONPath` \(located within the resource's YML file\) doesn't have unique values to act as a primary key. 

  
**Solution**: Use another column or combine multiple columns to achieve unique values



