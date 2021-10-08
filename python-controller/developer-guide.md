# Developer Guide

## How to create new API for Controller

A new API can be added to Controller. Follow the steps

## Background

All APIs remain in `routes.py`. If you want to create an independent API call then it is very easy. An independent API means when you don't want to log the process in the Foundry database. But if you want to create integrated API, means log the process in the Database then there are additional steps to be followed

### Independent API:

1. Write a python function to be called from API in a separate .py file `eg. sample_api.py`. 
2. Import `sample_api.py` in routes.py
3. Follow following structure to create api route in routes.py. \(_**This API will be similar to reboot API**_\)

```bash
@app.route('/controller/<new_api>', methods=['POST'])
@validate_request 
def new_api(): 
    status = <Function from sample.py>()
    return(jsonify({'message' : status}), 200)
```

1. It is necessary to apply validate\_request decorator, it will authenticate the API request.
2. Ensure that your function returns appropriate and meaningful response which will get returned as message to the client 



