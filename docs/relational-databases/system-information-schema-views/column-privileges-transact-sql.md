---
title: COLUMN_PRIVILEGES （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- COLUMN_PRIVILEGES
- COLUMN_PRIVILEGES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- COLUMN_PRIVILEGES view
- INFORMATION_SCHEMA.COLUMN_PRIVILEGES view
ms.assetid: 8ae29a85-2b77-48db-a2b9-a1720287b271
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c596539b5aff9c90947fb589627c8eabd134e6a3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750680"
---
# <a name="column_privileges-transact-sql"></a>COLUMN_PRIVILEGES (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  为具有当前数据库中的当前用户授受的权限的每列返回一行。  
  
 若要从这些视图中检索信息，请指定 INFORMATION_SCHEMA 的完全限定名称 **。**_view_name_。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**授权者**|**nvarchar （** 128 **）**|授权者。|  
|**被授权者**|**nvarchar （** 128 **）**|被授权者。|  
|**TABLE_CATALOG**|**nvarchar （** 128 **）**|表限定符。|  
|**TABLE_SCHEMA**|**nvarchar （** 128 **）**|包含该表的架构的名称。<br /><br /> **&#42;&#42; 重要 &#42;&#42;** 不要使用 INFORMATION_SCHEMA 视图来确定对象的架构。 INFORMATION_SCHEMA 视图仅表示对象的元数据的子集。 查找对象架构的唯一可靠方法是查询 sys.databases 目录视图。|  
|**TABLE_NAME**|**sysname**|表名。|  
|**COLUMN_NAME**|**sysname**|列名称。|  
|**PRIVILEGE_TYPE**|**varchar （** 10 **）**|特权的类型。|  
|**IS_GRANTABLE**|**varchar （** 3 **）**|指定被授权者是否可以向其他人授予权限。|  
  
## <a name="see-also"></a>另请参阅  
 [Transact-sql&#41;的系统视图 &#40;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [&#40;Transact-sql&#41;的信息架构视图](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. database_permissions &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [sys.server_permissions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)  
  
  
