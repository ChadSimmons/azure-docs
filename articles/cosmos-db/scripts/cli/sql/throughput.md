---
title: Perform throughput (RU/s) operations for Azure Cosmos DB Core (SQL) API resources
description: Azure CLI scripts for throughput (RU/s) operations for Azure Cosmos DB Core (SQL) API resources
author: markjbrown
ms.author: mjbrown
ms.service: cosmos-db
ms.subservice: cosmosdb-sql
ms.topic: sample
ms.date: 02/21/2022
---

# Throughput (RU/s) operations with Azure CLI for a database or container for Azure Cosmos DB Core (SQL) API

[!INCLUDE[appliesto-sql-api](../../../includes/appliesto-sql-api.md)]

The script in this article creates a Core (SQL) API database with shared throughput and a Core (SQL) API container with dedicated throughput, then updates the throughput for both the database and container. The script then migrates from standard to autoscale throughput then reads the value of the autoscale throughput after it has been migrated.

[!INCLUDE [quickstarts-free-trial-note](../../../../../includes/quickstarts-free-trial-note.md)]

[!INCLUDE [azure-cli-prepare-your-environment.md](../../../../../includes/azure-cli-prepare-your-environment.md)]

- This article requires version 2.12.1 or later of the Azure CLI. If using Azure Cloud Shell, the latest version is already installed.

## Sample script

[!INCLUDE [cli-launch-cloud-shell-sign-in.md](../../../../../includes/cli-launch-cloud-shell-sign-in.md)]

### Run the script

:::code language="azurecli" source="~/azure_cli_scripts/cosmosdb/sql/throughput.sh" id="FullScript":::

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
| [az cosmosdb create](/cli/azure/cosmosdb#az_cosmosdb_create) | Creates an Azure Cosmos DB account. |
| [az cosmosdb sql database create](/cli/azure/cosmosdb/sql/database#az_cosmosdb_sql_database_create) | Creates an Azure Cosmos Core (SQL) database. |
| [az cosmosdb sql container create](/cli/azure/cosmosdb/sql/container#az_cosmosdb_sql_container_create) | Creates an Azure Cosmos Core (SQL) container. |
| [az cosmosdb sql database throughput update](/cli/azure/cosmosdb/sql/database/throughput#az_cosmosdb_sql_database_throughput_update) | Update throughput for an Azure Cosmos Core (SQL) database. |
| [az cosmosdb sql container throughput update](/cli/azure/cosmosdb/sql/container/throughput#az_cosmosdb_sql_container_throughput_update) | Update throughput for an Azure Cosmos Core (SQL) container. |
| [az cosmosdb sql database throughput migrate](/cli/azure/cosmosdb/sql/database/throughput#az_cosmosdb_sql_database_throughput_migrate) | Migrate throughput for an Azure Cosmos Core (SQL) database. |
| [az cosmosdb sql container throughput migrate](/cli/azure/cosmosdb/sql/container/throughput#az_cosmosdb_sql_container_throughput_migrate) | Migrate throughput for an Azure Cosmos Core (SQL) container. |
| [az group delete](/cli/azure/resource#az_resource_delete) | Deletes a resource group including all nested resources. |

## Next steps

For more information on the Azure Cosmos DB CLI, see [Azure Cosmos DB CLI documentation](/cli/azure/cosmosdb).
