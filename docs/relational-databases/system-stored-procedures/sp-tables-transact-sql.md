---
title: sp_tables （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tables
- sp_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables
ms.assetid: 787a2fa5-87a1-49bd-938b-6043c245f46b
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 03a1d909dc1d3a89b68895e05953cc0ed0da2a7b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725511"
---
# <a name="sp_tables-transact-sql"></a>sp_tables (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asdw-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  返回可在当前环境中查询的对象的列表。 也就是说，返回任何表或视图（不包括同义词对象）。  
  
> [!NOTE]  
>  若要确定同义词的基对象的名称，请查询[sys.databases](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md)目录视图。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_tables [ [ @table_name = ] 'name' ]   
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @table_type = ] "type" ]   
     [ , [@fUsePattern = ] 'fUsePattern'];  
```  
  
## <a name="arguments"></a>自变量  
`[ @table_name = ] 'name'`用于返回目录信息的表。 *名称*为**nvarchar （384）**，默认值为 NULL。 支持通配符模式匹配。  
  
`[ @table_owner = ] 'owner'`用于返回目录信息的表的表所有者。 *所有者*为**nvarchar （384）**，默认值为 NULL。 支持通配符模式匹配。 如果未指定所有者，则遵循基础 DBMS 的默认表可见性规则。  
  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，如果当前用户拥有一个具有指定名称的表，则返回该表的列。 如果未指定所有者，且当前用户未拥有指定名称的表，则该过程查找由数据库所有者拥有的具有指定名称的表。 如果存在，则返回该表的列。  
  
`[ @table_qualifier = ] 'qualifier'`表限定符的名称。 *限定符*的值为**sysname**，默认值为 NULL。 各种 DBMS 产品支持表的三部分命名（_限定符_**。**_所有者_**。**_名称_）。 在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，此列表示数据库名称。 在某些产品中，该列表示表所在的数据库环境的服务器名。  
  
``[ , [ @table_type = ] "'type', 'type'" ]``以逗号分隔的值列表，它提供有关指定的表类型的所有表的信息。 其中包括**TABLE**、 **SYSTEMTABLE**和**VIEW**。 *类型*为**varchar （100）**，默认值为 NULL。  
  
> [!NOTE]  
>  每个表类型都必须用单引号引起来，整个参数必须用双引号引起来。 表类型必须大写。 如果 SET QUOTED_IDENTIFIER 为 ON，则每个单引号必须换成双引号，整个参数必须用单引号引起来。  
  
`[ @fUsePattern = ] 'fUsePattern'`确定下划线（_）、百分号（%）和方括号（[或]）字符是否解释为通配符。 有效值为 0（模式匹配为关闭状态）和 1（模式匹配为打开状态）。 *fUsePattern*的值为**bit**，默认值为1。  
  
## <a name="return-code-values"></a>返回代码值  
 无  
  
## <a name="result-sets"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|表限定符名称。 在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，此列表示数据库名称。 此字段可以为 NULL。|  
|**TABLE_OWNER**|**sysname**|表所有者名称。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，此列表示创建该表的数据库用户的名称。 此字段始终返回值。|  
|**TABLE_NAME**|**sysname**|表名。 此字段始终返回值。|  
|**TABLE_TYPE**|**varchar(32)**|表、系统表或视图。|  
|**备注**|**varchar （254）**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不为此列返回值。|  
  
## <a name="remarks"></a>备注  
 为达到最大互操作性，网关客户端应假定只有 SQL-92 标准的 SQL 模式匹配（% 和 _ 通配符字符）。  
  
 并不总是检查有关当前用户对特定表的读写权限的权限信息。 因此，访问得不到保障。 该结果集不仅包含表和视图，还包含网关的同名和别名，这些网关通往支持这些类型的 DBMS 产品。 如果**sp_server_info**的结果集中的服务器属性**ACCESSIBLE_TABLES**为 Y，则只返回当前用户可访问的表。  
  
 **sp_tables**等效于 ODBC 中的**SQLTables** 。 返回的结果按**TABLE_TYPE**、 **TABLE_QUALIFIER**、 **TABLE_OWNER**和**TABLE_NAME**进行排序。  
  
## <a name="permissions"></a>权限  
 需要对架构的 SELECT 权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-returning-a-list-of-objects-that-can-be-queried-in-the-current-environment"></a>A. 返回可在当前环境中查询的对象的列表  
 下面的示例返回可在当前环境中查询的对象的列表。  
  
```  
EXEC sp_tables ;  
```  
  
### <a name="b-returning-information-about-the-tables-in-a-specified-schema"></a>B. 返回与指定架构中的表相关的信息  
 以下示例将返回有关属于 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库中的 `Person` 架构的表的信息。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_tables   
   @table_name = '%',  
   @table_owner = 'Person',  
   @table_qualifier = 'AdventureWorks2012';  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-a-list-of-objects-that-can-be-queried-in-the-current-environment"></a>C. 返回可在当前环境中查询的对象的列表  
 下面的示例返回可在当前环境中查询的对象的列表。  
  
```  
EXEC sp_tables ;  
```  
  
### <a name="d-returning-information-about-the-tables-in-a-specified-schema"></a>D. 返回与指定架构中的表相关的信息  
 下面的示例返回有关数据库中的维度表的信息 `AdventureWorksPDW201` 。  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_tables   
   @table_name = 'Dim%',  
   @table_owner = 'dbo',  
   @table_qualifier = 'AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>另请参阅  
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

