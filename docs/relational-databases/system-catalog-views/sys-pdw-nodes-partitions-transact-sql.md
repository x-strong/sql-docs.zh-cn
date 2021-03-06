---
title: sys. pdw_nodes_partitions （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b4216752-4813-4b2c-b259-7d8ffc6cc190
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d0fc42e1ce8d15498caf89582b66549f4e083130
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "72305225"
---
# <a name="syspdw_nodes_partitions-transact-sql"></a>sys. pdw_nodes_partitions （Transact-sql）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  对于所有表的每个分区，以及[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]数据库中的大多数类型的索引，都包含一行。 所有表和索引都至少包含一个分区，无论它们是否已明确分区。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|分区的 id。 在数据库中是唯一的。|  
|object_id|**int**|此分区所属的对象的 id。 每个表或视图都至少包含一个分区。|  
|index_id|**int**|此分区所属的对象内的索引的 id。|  
|partition_number|**int**|拥有的索引或堆中从1开始的分区号。 对于[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]，此列的值为1。|  
|hobt_id|**bigint**|包含此分区的行的数据堆或B 树（HoBT）的 ID。|  
|行|**bigint**|此分区中的大约行数。 |  
|data_compression|**int**|指示每个分区的压缩状态：<br /><br /> 0 = NONE<br /><br /> 1 = ROW<br /><br /> 2 = PAGE<br /><br /> 3 = COLUMNSTORE|  
|data_compression_desc|**nvarchar(60)**|指示每个分区的压缩状态。 可能的值为 NONE、ROW 和 PAGE。|  
|pdw_node_id|**int**|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]节点的唯一标识符。|  
  
## <a name="permissions"></a>权限  
 需要 `CONTROL SERVER` 权限。  
  
## <a name="examples-sssdwfull-and-sspdw"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

### <a name="example-a-display-rows-in-each-partition-within-each-distribution"></a>示例 A：显示每个分布区中每个分区的行 

**适用于：** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]
 
若要显示每个分布区中每个分区的行数，请使用[DBCC PDW_SHOWPARTITIONSTATS （SQL Server PDW）](../../t-sql/database-console-commands/dbcc-pdw-showpartitionstats-transact-sql.md) 。

### <a name="example-b-uses-system-views-to-view-rows-in-each-partition-of-each-distribution-of-a-table"></a>示例 B：使用系统视图查看表的每个分布区中每个分区的行

**适用对象：** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]
 
此查询返回表`myTable`的每个分布区中每个分区的行数。  
 
```sql  
SELECT o.name, pnp.index_id, pnp.partition_id, pnp.rows,   
    pnp.data_compression_desc, pnp.pdw_node_id  
FROM sys.pdw_nodes_partitions AS pnp  
JOIN sys.pdw_nodes_tables AS NTables  
    ON pnp.object_id = NTables.object_id  
AND pnp.pdw_node_id = NTables.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON NTables.name = TMap.physical_name 
    AND substring(TMap.physical_name,40, 10) = pnp.distribution_id 
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
WHERE o.name = 'myTable'  
ORDER BY o.name, pnp.index_id, pnp.partition_id;  
```    
  
## <a name="see-also"></a>另请参阅  
 [SQL 数据仓库和并行数据仓库目录视图](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  

