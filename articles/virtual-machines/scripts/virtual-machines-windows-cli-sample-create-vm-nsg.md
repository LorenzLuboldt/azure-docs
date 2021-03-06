---
title: Azure CLI Script Sample - Create two VMs with an internal and external NSG | Microsoft Docs
description: Azure CLI Script Sample - Create two VMs with internal and external NSG
services: virtual-machines-windows
documentationcenter: virtual-machines
author: rickstercdn
manager: timlt
editor: tysonn
tags: 

ms.assetid:
ms.service: virtual-machines-windows
ms.devlang: azurecli
ms.topic: article
ms.tgt_pltfrm: vm-windows
ms.workload: infrastructure
ms.date: 02/23/2017
ms.author: rclaus
---

# Secure network traffic between virtual machines

This script creates two virtual machines and secures incoming traffic to both. One virtual machine is accessible on the internet and has a network security group (NSG) configured to allow traffic on port 3389 and port 80. The second virtual machine is not accessible on the internet, and has an NSG configured to only allow traffic from the first virtual machine. 

[!INCLUDE [sample-cli-install](../../../includes/sample-cli-install.md)]

[!INCLUDE [quickstarts-free-trial-note](../../../includes/quickstarts-free-trial-note.md)]

## Sample script

[!code-azurecli[main](../../../cli_scripts/virtual-machine/create-vm-nsg/create-windows-vm-nsg.sh "Create VM with NSG")]

## Clean up deployment 

Run the following command to remove the resource group, VM, and all related resources.

```azurecli
az group delete --name myResourceGroup --yes
```

## Script explanation

This script uses the following commands to create a resource group, virtual machine, and all related resources. Each command in the table links to command specific documentation.

| Command | Notes |
|---|---|
| [az group create](https://docs.microsoft.com/cli/azure/group#create) | Creates a resource group in which all resources are stored. |
| [az network vnet create](https://docs.microsoft.com/cli/azure/network/vnet#create) | Creates an Azure virtual network and subnet. |
| [az network vnet subnet create](https://docs.microsoft.com/cli/azure/network/vnet/subnet#create) | Creates a subnet. |
| [az vm create](https://docs.microsoft.com/cli/azure/vm#create) | Creates the virtual machine and connects it to the network card, virtual network, subnet, and NSG. This command also specifies the virtual machine image to be used, and administrative credentials.  |
| [az network nsg rule update](https://docs.microsoft.com/cli/azure/network/nsg/rule#update) | Updates an NSG rule. In this sample, the back-end rule is updated to pass through traffic only from the front-end subnet. |
| [az network nsg rule list](https://docs.microsoft.com/cli/azure/network/nsg/rule#list) | Returns information about a network security group rule. In this sample, the rule name is stored in a variable for use later in the script. |
| [az group delete](https://docs.microsoft.com/cli/azure/vm/extension#set) | Deletes a resource group including all nested resources. |

## Next steps

For more information on the Azure CLI, see [Azure CLI documentation](https://docs.microsoft.com/cli/azure/overview).

Additional virtual machine CLI script samples can be found in the [Azure Windows VM documentation](../windows/cli-samples.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).
