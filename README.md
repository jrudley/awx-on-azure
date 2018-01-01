Overview
====

Deploy AWX environment to Azure VM.

How to deploy to Azure
====

You need [Azure CLI 2.0](https://docs.microsoft.com/en-us/cli/azure/overview?view=azure-cli-latest).

First you should fill `parameters.publicKey.value` in `azure/parameters.json` by your public key.

```json
{
    ...
    "parameters": {
        ...
        "publicKey": {
            "value": "ssh-rsa ..."
        },
        ...
```

Then you can deploy like following commands.

```bash
az login
az group create -n <resource group name> -l japaneast
az group deployment create -g <resource group name> --template-file azure/zuredeploy.json --parameters @azure/arameters.json
```

After deployment finished, you need wait a moment until finish provisioning.