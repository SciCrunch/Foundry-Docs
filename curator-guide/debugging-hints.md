# Troubleshooting Hints

## **Only 1 record has been ingested (no errors in ingest)**

1\) It's most likely the case that the specified column for `primaryKeyJSONPath` (located within the resource's YML file) doesn't have unique values to act as a primary key.&#x20;

**Solution**: Use another column or combine multiple columns to achieve unique values

2\) If ingesting data from a CSV, it's most likely the case that the column that you're using as the primary key contains a invisible character which results in the code not being able to identify the specified column.

**Solution:** Run the following command on the CSV file: `sed -i '1s/^\xEF\xBB\xBF//' {fileName}`

## **The number of ingested records doesn't match the number of input records (no errors in ingest)**

This is most likely due to records with the same primary key. It's most likely the case that the specified column for `primaryKeyJSONPath` (located within the resource's YML file) doesn't have unique values to act as a primary key.&#x20;

\
**Solution**: Use another column or combine multiple columns to achieve unique values

## If half of the records error out with no errors shown in the log file (In Production)

This is most likely due to the Primary Consumer not being fully up and running.&#x20;



**Solution:** Talk with either Jeff or Burak on the status of the Primary Consumer
