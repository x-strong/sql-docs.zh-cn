---
title: 使用包含的数据库与可用性组
description: 如何使用包含的数据库与 Always On 可用性组
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- contained database, AlwaysOnAvailabilityGroups
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26e92d38188b02c5a2ce0025cc2d33fccc5c6728
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2020
ms.locfileid: "67988421"
---
# <a name="use-contained-databases-with-always-on-availability-groups"></a>使用包含的数据库与 Always On 可用性组 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  本主题包含将包含数据库用于 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的相关信息。  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a>先决条件  
  
-   在将包含数据库添加到某一可用性组之前，请确保在承载该可用性组的可用性副本的每个服务器实例上 **contained database authentication** 服务器选项都设置为 **1** 。 有关详细信息，请参阅 [contained database authentication 服务器配置选项](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) 和 [服务器配置选项 (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)的相关信息。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 相关任务  
  
-   [服务器配置选项 (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [包含的数据库](../../../relational-databases/databases/contained-databases.md)  
  
  
