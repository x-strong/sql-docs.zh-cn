---
title: 删除 Sybase 组件的 SSMA （SybaseToSQL） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: aec09593-17d9-4ec2-ac56-3cd8851406fd
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0c76b6b2e4e5295bf7db2d7857a73223fc6f8c7e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "68028640"
---
# <a name="removing-ssma-for-sybase-components-sybasetosql"></a>删除 SSMA for Sybase 组件 (SybaseToSQL)
将数据库从 Sybase 自适应服务器企业版（ASE）迁移到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之后，你可能想要卸载 SSMA 组件。 你可以随时卸载客户端组件，但不能从中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]卸载扩展包，除非你确定已迁移的数据库不再使用**sysdb**数据库的**ssma_syb**架构中的函数。  
  
## <a name="uninstalling-the-ssma-for-sybase-client"></a>正在卸载 Sybase 客户端的 SSMA  
可以使用 "**添加或删除程序**" 卸载 SSMA。  
  
**卸载 SSMA**  
  
1.  在“控制面板”中，打开“添加或删除程序”  。  
  
2.  选择 "**为 Sybase Microsoft SQL Server 迁移助手**"，然后单击 "**删除**"。  
  
3.  若要确认是否要卸载 SSMA，请单击 **"是"**。  
  
## <a name="uninstalling-the-extension-pack"></a>正在卸载扩展包  
如果确定迁移的数据库不使用**ssma_syb sysdb**架构中的对象，则可以使用 "**添加或删除程序**" 删除扩展包。  
  
卸载扩展包  
  
1.  在“控制面板”中，打开“添加或删除程序”  。  
  
2.  选择 " **Microsoft SQL Server 迁移助手作为 Sybase Extension Pack**"，然后单击 "**删除**"。  
  
3.  若要确认是否要卸载扩展包，请单击 **"是"**。  
  
4.  在 "带有实用程序数据库脚本的实例" 页上，单击 "**下一步**"。  
  
5.  在 "连接参数" 页上，选择身份验证方法，然后单击 "**下一步**"。  
  
    Windows 身份验证将使用您的 Windows 凭据来尝试登录到 SQL Server 的实例。 如果选择 SQL Server 身份验证，则必须输入 SQL Server 登录名和密码。  
  
6.  在 "操作已完成" 页上，单击 **"确定"**。  
  
7.  在 "完成" 页上，单击 "**退出**"。  
  
卸载后，可以通过使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]确认是否已删除**ssma_syb sysdb**架构（可能为整个**sysdb**数据库）。 但是，如果您使用其他 SSMA 产品，它们也使用**sysdb**数据库。 如果数据库存在并且您确定没有其他数据库引用此数据库中的对象，则可以分离该数据库。  
  
## <a name="see-also"></a>另请参阅  
[为 Sybase 客户端 &#40;SybaseToSQL&#41;安装 SSMA](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[在 SQL Server 上安装 SSMA 组件 &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
  
