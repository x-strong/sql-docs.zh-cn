---
title: sp_clean_db_free_space （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_clean_db_free_space_TSQL
- sp_clean_db_free_space
dev_langs:
- TSQL
helpviewer_keywords:
- sp_clean_db_free_space
- ghost records
ms.assetid: faa96f7e-be92-47b1-8bc5-4dbba5331655
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ea9690011e963e6374b562f37d64573546a170c3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85871112"
---
# <a name="sp_clean_db_free_space-transact-sql"></a>sp_clean_db_free_space (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  删除因 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据修改例程而留在数据库页上的残留信息。 sp_clean_db_free_space 清除数据库中所有文件的所有页。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_clean_db_free_space   
[ @dbname ] = 'database_name'   
[ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>参数  
 [ @dbname =] "*database_name*"  
 要清理的数据库的名称。 *dbname*为**sysname** ，且不能为 NULL。  
  
 [ @cleaning_delay =] "*delay_in_seconds*"  
 指定各次页清理之间的延迟间隔。 这会有助于减轻对 I/O 系统的影响。 *delay_in_seconds*的**整数为 int** ，默认值为0。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="remarks"></a>备注  
 删除表的操作或更新操作导致行移动可以立即通过删除对该行的引用来释放页上的空间。 但是，在某些情况下，该行仍然作为虚影记录而保留在数据页上。 后台进程定期清除虚影记录。 不会在响应查询时返回该残留数据 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。 但是，在数据或备份文件处于其物理安全性面临风险的环境中时，可以使用 sp_clean_db_free_space 来清除虚影记录。  
  
 运行 sp_clean_db_free_space 所需的时间依文件大小、磁盘的可用空间和容量而定。 由于运行 sp_clean_db_free_space 对 I/O 活动有较大的影响，我们建议您在常规运行时间之外运行此过程。  
  
 鉴于您要运行 sp_clean_db_free_space，我们建议您创建完整数据库备份。  
  
 相关的[sp_clean_db_file_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-file-free-space-transact-sql.md)存储过程可以清除单个文件。  
  
## <a name="permissions"></a>权限  
 需要 db_owner 数据库角色中的成员身份。  
  
## <a name="examples"></a>示例  
 下面的示例从 `AdventureWorks2012` 数据库中清除所有残留信息。  
  
```  
USE master;  
GO  
EXEC sp_clean_db_free_space   
@dbname = N'AdventureWorks2012' ;  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据库引擎存储过程 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)
 <br>[虚影清除过程指南](../ghost-record-cleanup-process-guide.md) 
  
  
