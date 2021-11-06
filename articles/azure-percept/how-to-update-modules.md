---
title: Update Azure Percept Modules over IoT Hub
description: Learn how to update Azure Percept Audio and Azure Percept Vision Modules of your Azure Percept DK
author: nimix
ms.author: nimix
ms.service: azure-percept
ms.topic: how-to
ms.date: 11/06/2021
ms.custom: template-how-to
---

# Update Azure Percept Modules

Follow this guide to learn how to update the Azure Percept Audio and Vision Module of your Azure Percept DK through the IoT Hub.

## Prerequisites

- Azure Percept DK (devkit)
- [Azure subscription](https://azure.microsoft.com/free/)
- [Azure Percept DK setup experience](./quickstart-percept-dk-set-up.md): you connected your dev kit to a Wi-Fi network, created an IoT Hub, and connected your dev kit to the IoT Hub

## Introduction

The Azure Percept DK Module which acts as an IoT Edge Device, executes custom modules to interact with devices connected to your development kit. These modules are containers, which contain logic required to interact with the device.

## Identify Container Tags

1. The following containers are provided to run with the Azure Percept DK:

- [mcr.microsoft.com/azureedgedevices/webstreammodule](https://mcr.microsoft.com/v2/azureedgedevices/webstreammodule/tags/list)
- [mcr.microsoft.com/azureedgedevices/devmmclientmodule](https://mcr.microsoft.com/v2/azureedgedevices/devmmclientmodule/tags/list)
- [mcr.microsoft.com/azureedgedevices/azureearspeechclientmodule](https://mcr.microsoft.com/v2/azureedgedevices/azureearspeechclientmodule/tags/list)
- [mcr.microsoft.com/azureedgedevices/azureeyemodule](https://mcr.microsoft.com/v2/azureedgedevices/azureeyemodule/tags/list)
- [mcr.microsoft.com/azureedgedevices/imagecapturingmodule](https://mcr.microsoft.com/v2/azureedgedevices/imagecapturingmodule/tags/list)
- [mcr.microsoft.com/azureedgedevices/hostipmodule](https://mcr.microsoft.com/v2/azureedgedevices/hostipmodule/tags/list)
  
1. Every container is linked to the current tag list, choose the Module you want to update and identify the Tag you want to update to

> [!NOTE]
> Azure Percept Module Containers are not listed on Docker Hub

> [!CAUTION]
> It's recommended to only update **azureeyemodule** and **azureearspeechclientmodule** otherwise this might cause that the device to not respond through the Azure Percept Studio anymore or alter its behaviour. You can revert your change through another deployment at any time.

> [!CAUTION]
> Ensure the container tag exists as otherwise this module will not be responding anymore

## Verify Module Version from Azure Percept Studio

1. From the Azure Percept Studio, select **Devices**
 
1. Navigate to the Device you want to update

1. You can investigate the currently installed version under the **Vision** and **Speech** Tab

> [!NOTE]
> You can directly jump to the device, to update the modules by using **Open device in IoT Hub** in the Azure Percept Studio Device View

## Update Modules from Azure IoT Hub

1. Navigate to the Azure IoT Hub that you are using for your Azure Percept device. 

1. Select **IoT Edge** and navigate to the Device which modules you want to update

1. Use **Set modules** to override the current module configuration

  1. To update the Vision Module select **azureeyemodule** and update the Image URI to contain the new version tag to which you want to up-/downgrade to

  1. To update the Speech Module select **azureearspeechclientmodule**

1. Click **Review + Create** to review the new Device Configuration and click **Create** to submit the deployment

> [!NOTE]
> It might take a while until Azure Percept Studio shows the updated version, as the Azuer Percept DK needs to retrive the new container image first

> [!NOTE]
> From the **IoT Edge** view of the IoT Hub you can update multiple devices at once, using the **IoT Edge Deployments** you can find further informations [here](../iot-edge/module-composition.md)

## Next steps

Your dev kit modules are now successfully updated. You may continue development and operation with your dev kit.
