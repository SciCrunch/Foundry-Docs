# Helper Scripts for Foundry Ingestion

### Introduction

In order to assist curators in the configuration and testing of new data and information resources a number of helper scripts have been developed:

1. test\_config.sh
2. test\_transform.sh
3. test\_qc.sh
4. update\_source.sh
5. remove\_source.sh

These scripts aggregate a number of actions that curators normally perform including GitHub actions (pulling updated descriptors, committing sample data and pushing to GitHub) and Foundry actions. Currently, GitHub actions are configured based on the AWS environment they are running in (default on in production environment \[aws linux with default ec2-user] and off in development \[any other environment - e.g. ubuntu with the ubuntu user]).

```
DOGIT=0
if [[ "$OSTYPE" == "linux-gnu"* ]]; then
if [[ "$HOME" == "/home/ec2-user" ]]; then
    DOGIT=1
fi
fi
```

### [test\_config.sh](https://github.com/SciCrunch/Foundry-Data/blob/master/Scripts/test\_config.sh)

This wrapper script tests the configuration of the resource's yml file. Producing sample data converted into json format

```
[Template]: ./test_config.sh {data resource name} {number of records to show}
[Example]: ./test_config.sh SCR_017041-Datasets-SPARC 50
```

### [test\_transform.sh](https://github.com/SciCrunch/Foundry-Data/blob/master/Scripts/test\_transform.sh)

This wrapper script tests the transformation script on the converted sample data

```
[Template]: ./test_transform.sh {data resource name}
[Example]: ./test_transform.sh SCR_017041-Datasets-SPARC
```

### test\_qc.sh

This wrapper script tests the QA/QC YAML file to enure it is properly formatted and structured.

```
// Some code
```

### [update\_source.sh](https://github.com/SciCrunch/Foundry-Data/blob/master/Scripts/update\_source.sh)

This wrapper script regenerates the source descriptor of the resource, removes the descriptor stored in Foundry, and adds the updated version back in.

```
[Template]: ./update_source.sh {data resource name} {number of records to show}
[Example]: ./update_source.sh SCR_017041-Datasets-SPARC
```

### [remove\_source.sh](https://github.com/SciCrunch/Foundry-Data/blob/master/Scripts/remove\_source.sh)

This wrapper script removes the resource from Foundry.

```
[Template]: ./remove_source.sh {data resource name}
[Example]: ./remove_source.sh SCR_017041-Datasets-SPARC
```
