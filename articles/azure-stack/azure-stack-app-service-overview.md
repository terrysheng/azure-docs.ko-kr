---
title: App Service Overview - Azure Stack | Microsoft Docs
description: Overview of App Service on Azure Stack
services: azure-stack
documentationcenter: 
author: apwestgarth
manager: stefsch
editor: 
ms.assetid: 
ms.service: azure-stack
ms.workload: app-service
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 3/1/2017
ms.author: anwestg
translationtype: Human Translation
ms.sourcegitcommit: cf55a0b4f61c971cedee602575f73d39c70f9edb
ms.openlocfilehash: 17f377e023255dc4629211f41ae0539902ff19b7
ms.lasthandoff: 03/01/2017


---

# <a name="app-service-on-azure-stack-overview"></a>App Service on Azure Stack Overview
    
> [!IMPORTANT] 
> This topic applies only to Azure Stack Technical Preview 2.
>

App Service on Azure Stack is the Azure offering brought to Azure Stack. The App Service on Azure Stack installer will create the following set of role instances:
*  Controller;
*  Management (Two instances will be created);
*  Front-End;
*  Publisher;
*  Worker (in Shared mode)

In addition, the App Service on Azure Stack installer will create a file server.
    
Although you can add more instances for each of the role types, remember that there is not much space for VMs in Technical Preview 2. The capabilities for App Service on Azure Stack Technical Preview 2 have been extended adding more capabilities around managing the system and hosting Web, Mobile, and API Apps.

![App Service in the Azure Stack Portal][1]

## <a name="limitations-of-the-technical-preview"></a>Limitations of the Technical Preview

There is no support for the App Service on Azure Stack preview releases, although we do monitor the Azure Stack MSDN Forum. Don't put production workloads on this preview release. There is also no upgrade between App Service on Azure Stack preview releases. The primary purposes of these preview releases are to show what we are providing and to obtain feedback. 

## <a name="what-is-an-app-service-plan"></a>What is an App Service Plan?

The App Service resource provider uses the same code that Azure App Service uses. As a result, some common concepts are worth describing. In App Service, the pricing container for applications is called the App Service plan. It represents the set of dedicated virtual machines used to hold your apps. Within a given subscription, you can have multiple App Service plans. 

In Azure, there are shared and dedicated workers. A shared worker supports high-density multitenant app hosting and there is only one set of shared workers. Dedicated servers are only used by one tenant and come in three sizes: small, medium, and large. The needs of on-premises customers can't always be described by using those terms. In App Service on Azure Stack, resource provider administrators can define the worker tiers they want to make available.  Therefore having multiple sets of shared workers or different sets of dedicated workers based on their unique hosting needs. Using those worker tier definitions, they can then define their own pricing SKUs.

## <a name="portal-features"></a>Portal Features

App Service on Azure Stack uses the same UI that Azure App Service uses, as is true with the back end. Some features are disabled and aren't yet functional in Azure Stack, because Azure-specific expectations or services that those features require aren't yet available in Azure Stack. 

## <a name="next-steps"></a>Next steps

- [Before you get started with App Service on Azure Stack](azure-stack-app-service-before-you-get-started.md)
- [Install the App Service Resource Provider](azure-stack-app-service-deploy.md)

You can also try out other [platform as a service (PaaS) services](azure-stack-tools-paas-services.md), like the [SQL Server resource provider](azure-stack-sql-resource-provider-deploy.md) and [MySQL resource provider](azure-stack-mysql-resource-provider-deploy.md).

<!--Image references-->
[1]: ./media/azure-stack-app-service-overview/AppService_Portal.png

