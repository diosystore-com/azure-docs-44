---
title: Install the Microsoft Dev Box Azure CLI extension
titleSuffix: Microsoft Dev Box
description: Learn how to install the Azure CLI and the Microsoft Dev Box CLI extension so you can create Dev Box resources from the command line.
services: dev-box
ms.service: dev-box
ms.topic: how-to
ms.author: rosemalcolm
author: RoseHJM
ms.date: 03/19/2023
Customer intent: As a dev infra admin, I want to install the Dev Box CLI extension so that I can create Dev Box resources from the command line.
---

# Configure Microsoft Dev Box from the command-line with the Azure CLI extension

In addition to the Azure admin portal and the developer portal, you can use the Dev Box Azure CLI extension to create resources. Microsoft Dev Box and Azure Deployment Environments use the same Azure CLI extension, which is called `devcenter`.

## Install the Dev Box CLI extension 

To install the Dev Box Azure CLI extension, you first need to install the Azure CLI. The following steps show you how to install the Azure CLI, then the Dev Box CLI extension.

1. Download and install the [Azure CLI](/cli/azure/install-azure-cli).

1. Install the Dev Box CLI extension
``` azurecli
az extension add --name devcenter
```
1. Check that the `devcenter` extension is installed 
``` azurecli
az extension list
```
### Update the Dev Box CLI extension
You can update the Dev Box CLI extension if you already have it installed.

To update a version of the extension that's  installed
``` azurecli
az extension update --name devcenter
```
### Remove the Dev Box CLI extension

To remove the extension, use the following command
```azurecli
az extension remove --name devcenter
```

## Get started with the Dev Box CLI extension

You might find the following commands useful as you work with the Dev Box CLI extension.

1. Sign in to Azure CLI with your work account.

    ```azurecli
    az login
    ```

1. Set your default subscription to the subscription where you're creating your specific Dev Box resources.

    ```azurecli
    az account set --subscription {subscriptionId}
    ```

1. Set default resource group. Setting a default resource group means you don't need to specify the resource group for each command.

    ```azurecli
    az configure --defaults group={resourceGroupName}
    ```

1. Get Help for a command

    ```azurecli
    az devcenter admin --help
    ```

## Next steps

For complete command listings, refer to the [Microsoft Dev Box and Azure Deployment Environments Azure CLI documentation](https://aka.ms/CLI-reference).