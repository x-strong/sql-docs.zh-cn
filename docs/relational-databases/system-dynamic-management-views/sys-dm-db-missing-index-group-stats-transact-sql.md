---
title: sys. dm_db_missing_index_group_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_group_stats_TSQL
- sys.dm_db_missing_index_group_stats
- dm_db_missing_index_group_stats_TSQL
- dm_db_missing_index_group_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_missing_index_group_stats dynamic management view
- missing indexes feature [SQL Server], sys.dm_db_missing_index_group_stats dynamic management view
ms.assetid: c2886986-9e07-44ea-a350-feeac05ee4f4
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2879f5678c315d3e3921813a5d26a6c6034aa05f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85718816"
---
# <a name="sysdm_db_missing_index_group_stats-transact-sql"></a>sys.dm_db_missing_index_group_stats (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  返回缺失索引组的摘要信息，不包括空间索引。  
  
 在 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 中，动态管理视图不能公开将影响数据库包含的信息，也不能公开有关用户可以访问的其他数据库的信息。 为了避免公开此信息，每个包含不属于所连接的租户的数据的行都将被筛选掉。  
    
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**group_handle**|**int**|标识缺失索引组。 此标识符在服务器中是唯一的。<br /><br /> 其他列提供有关组中的索引被视为缺失的所有查询的信息。<br /><br /> 一个索引组仅包含一个索引。|  
|**unique_compiles**|**bigint**|将从该缺失索引组受益的编译和重新编译数。 许多不同查询的编译和重新编译可影响该列值。|  
|**user_seeks**|**bigint**|由可能使用了组中建议索引的用户查询所导致的查找次数。|  
|**user_scans**|**bigint**|由可能使用了组中建议索引的用户查询所导致的扫描次数。|  
|**last_user_seek**|**datetime**|由可能使用了组中建议索引的用户查询所导致的上次查找日期和时间。|  
|**last_user_scan**|**datetime**|由可能使用了组中建议索引的用户查询所导致的上次扫描日期和时间。|  
|**avg_total_user_cost**|**float**|可通过组中的索引减少的用户查询的平均成本。|  
|**avg_user_impact**|**float**|实现此缺失索引组后，用户查询可能获得的平均百分比收益。 该值表示如果实现此缺失索引组，则查询成本将按此百分比平均下降。|  
|**system_seeks**|**bigint**|由可能使用了组中建议索引的系统查询（如自动统计信息查询）所导致的查找次数。 有关详细信息，请参阅[Auto Stats 事件类](../../relational-databases/event-classes/auto-stats-event-class.md)。|  
|**system_scans**|**bigint**|由可能使用了组中建议索引的系统查询所导致的扫描次数。|  
|**last_system_seek**|**datetime**|由可能使用了组中建议索引的系统查询所导致的上次系统查找日期和时间。|  
|**last_system_scan**|**datetime**|由可能使用了组中建议索引的系统查询所导致的上次系统扫描日期和时间。|  
|**avg_total_system_cost**|**float**|可通过组中的索引减少的系统查询的平均成本。|  
|**avg_system_impact**|**float**|实现此缺失索引组后，系统查询可能获得的平均百分比收益。 该值表示如果实现此缺失索引组，则查询成本将按此百分比平均下降。|  
  
## <a name="remarks"></a>备注  
 将根据每个查询执行，而不是根据每个查询编译或重新编译来更新由 **sys.dm_db_missing_index_group_stats** 返回的信息。 使用情况统计信息不会持久保留，并且只保留到重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 前。 如果数据库管理员要在服务器回收后保留使用情况统计信息，则应该定期制作缺失索引信息的备份副本。  

  >[!NOTE]
  >此 DMV 的结果集限制为600行。 每一行都包含一个缺失索引。 如果缺少超过600个索引，则应该解决现有的缺失索引，以便可以查看更新的索引。
  
## <a name="permissions"></a>权限  
 若要查询此动态管理视图，必须授予用户 VIEW SERVER STATE 权限或隐含 VIEW SERVER STATE 权限的任何权限。  
  
## <a name="examples"></a>示例  
 以下示例阐释了如何使用 **sys.dm_db_missing_index_group_stats** 动态管理视图。  
  
### <a name="a-find-the-10-missing-indexes-with-the-highest-anticipated-improvement-for-user-queries"></a>A. A. 查找十个具有最高用户查询预期提高的缺失索引  
 下面的查询确定了将生成最高预期累计提高的十个缺失索引，按降序排列。  
  
```  
SELECT TOP 10 *  
FROM sys.dm_db_missing_index_group_stats  
ORDER BY avg_total_user_cost * avg_user_impact * (user_seeks + user_scans)DESC;  
```  
  
### <a name="b-find-the-individual-missing-indexes-and-their-column-details-for-a-particular-missing-index-group"></a>B. 查找特定缺失索引组的单个缺失索引及其列详细信息  
 下面的查询确定哪些缺失索引构成特定缺失索引组，并显示其列详细信息。 针对此示例，缺失索引组句柄为 24。  
  
```  
SELECT migs.group_handle, mid.*  
FROM sys.dm_db_missing_index_group_stats AS migs  
INNER JOIN sys.dm_db_missing_index_groups AS mig  
    ON (migs.group_handle = mig.index_group_handle)  
INNER JOIN sys.dm_db_missing_index_details AS mid  
    ON (mig.index_handle = mid.index_handle)  
WHERE migs.group_handle = 24;  
```  
  
 此查询提供缺失索引的数据库、架构和表的名称。 它还提供应该用于索引键的列的名称。 写入 CREATE INDEX DDL 语句以实现缺失索引时，请在 CREATE INDEX 语句的 ON 子句中先列出相等列，然后再列出不等列 \<*table_name*> 。 应该在 CREATE INDEX 语句的 INCLUDE 子句中列出包含列。 若要确定相等列的有效顺序，请基于其选择性排序，首先列出选择性最强的列（列列表中的最左侧）。  
  
## <a name="see-also"></a>另请参阅  
 [sys. dm_db_missing_index_columns &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys. dm_db_missing_index_details &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys. dm_db_missing_index_groups &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)  
  
  
