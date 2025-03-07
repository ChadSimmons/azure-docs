---
title: Create an Azure Cosmos account with virtual network service endpoints
description: Create an Azure Cosmos account with virtual network service endpoints
author: markjbrown
ms.author: mjbrown
ms.service: cosmos-db
ms.topic: sample
ms.date: 02/21/2022
---

# Create an Azure Cosmos account with virtual network service endpoints using Azure CLI

[!INCLUDE[appliesto-all-apis](../../../includes/appliesto-all-apis.md)]

The script in this article creates a new virtual network with a front and back end subnet and enables service endpoints for `Microsoft.AzureCosmosDB`. It then retrieves the resource ID for this subnet and applies it to the Azure Cosmos account and enables service endpoints for the account.

This script uses a Core (SQL) API account. To use this sample for other APIs, apply the `enable-virtual-network` and `virtual-network-rules` parameters in the script below to your API specific script.

[!INCLUDE [quickstarts-free-trial-note](../../../../../includes/quickstarts-free-trial-note.md)]

[!INCLUDE [azure-cli-prepare-your-environment.md](../../../../../includes/azure-cli-prepare-your-environment.md)]

- This article requires version 2.9.1 or later of the Azure CLI. If using Azure Cloud Shell, the latest version is already installed.

## Sample script

[!INCLUDE [cli-launch-cloud-shell-sign-in.md](../../../../../includes/cli-launch-cloud-shell-sign-in.md)]

### Run the script

:::code language="azurecli" source="~/azure_cli_scripts/cosmosdb/common/service-endpoints.sh" id="FullScript":::

## Clean up resources

[!INCLUDE [cli-clean-up-resources.md](../../../../../includes/cli-clean-up-resources.md)]

```azurecli
az group delete --name $resourceGroup
```

## Sample reference

This script uses the following commands. Each command in the table links to command specific documentation.

| Command | Notes |
|---|---|
| [az group create](/cli/azure/group#az_group_create) | Creates a resource group in which all resources are stored. |
| [az network vnet create](/cli/azure/network/vnet#az_network_vnet_create) | Creates an Azure virtual network. |
| [az network vnet subnet create](/cli/azure/network/vnet/subnet#az_network_vnet_subnet_create) | Creates a subnet for an Azure virtual network. |
| [az network vnet subnet show](/cli/azure/network/vnet/subnet#az_network_vnet_subnet_show) | Returns a subnet for an Azure virtual network. |
| [az cosmosdb create](/cli/azure/cosmosdb#az_cosmosdb_create) | Creates an Azure Cosmos DB account. |
| [az group delete](/cli/azure/resource#az_resource_delete) | Deletes a resource group including all nested resources. |

## Next steps

For more information on the Azure Cosmos DB CLI, see [Azure Cosmos DB CLI documentation](/cli/azure/cosmosdb).

For Azure CLI samples for specific APIs see:

- [CLI Samples for Cassandra](../../../cassandra/cli-samples.md)
- [CLI Samples for Gremlin](../../../graph/cli-samples.md)
- [CLI Samples for MongoDB API](../../../mongodb/cli-samples.md)
- [CLI Samples for SQL](../../../sql/cli-samples.md)
- [CLI Samples for Table](../../../table/cli-samples.md)
