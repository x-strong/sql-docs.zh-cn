---
title: 最小化日志文件空间使用情况 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- log file space in RDS [ADO]
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
author: rothja
ms.author: jroth
ms.openlocfilehash: 1eca3db07301ca45c898f21f558339e5f2ab93e1
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747872"
---
# <a name="minimizing-log-file-space-usage"></a>最大程度降低日志文件空间使用
如果 SQL Server 数据库中有大量活动，则日志文件可能会快速填充（因此会停止服务器）。 你可以将日志文件设置为**在检查点截断**，以显著延长数据库日志文件的生存期。  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，Windows 操作系统中不再包含 RDS 服务器组件（有关详细信息，请参阅 Windows 8 和[Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416)）。 在 Windows 的未来版本中将删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>在 Microsoft SQL Server 6.5 中启用检查点截断  
  
1.  启动 Microsoft SQL Server Enterprise 管理器 "，打开服务器树，然后打开" 数据库设备 "树。  
  
2.  双击要启用此功能的数据库的名称。  
  
3.  从 "**数据库**" 选项卡中，选择 "**截断**"。  
  
4.  在 "**选项**" 选项卡中，选择 "**截断检查点日志**"，然后单击 **"确定"**。  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>在 Microsoft SQL Server 7.0 中启用检查点截断  
  
1.  启动 Microsoft SQL Server Enterprise 管理器 "，打开服务器树，然后打开" 数据库 "树。  
  
2.  右键单击要在其上启用此功能的数据库的名称，然后选择 "**属性**"。  
  
3.  在 "**选项**" 选项卡中，选择 "**截断检查点日志**"，然后单击 **"确定"**。  
  
 有关**截断检查点**功能的详细信息，请参阅 Microsoft SQL Server 文档。  
  
## <a name="see-also"></a>另请参阅  
 [RDS 基础知识](../../../ado/guide/remote-data-service/rds-fundamentals.md)


