---
title: sys. dm_exec_distributed_sql_requests （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- sys.dm_exec_distributed_requests management view
- dm_exec_distributed_requests management view
ms.assetid: d065dc01-35d4-472f-9554-53ac41e7d104
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0bfaaa65c08155263c15a1e4e4ddf17c20913e66
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827971"
---
# <a name="sysdm_exec_distributed_sql_requests-transact-sql"></a>sys.dm_exec_distributed_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  将有关所有 SQL 查询分发的信息保存为查询中的 SQL 步骤的一部分。  此视图显示最后一个1000请求的数据;活动请求始终具有此视图中的数据。  
  
|列名|数据类型|说明|范围|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|execution_id 和 step_index 构成此视图的键。 与请求关联的唯一数字 id。|请参阅 sys.databases 中的 ID [dm_exec_requests &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)|  
|step_index|**int**|此分发所属的查询步骤的索引。|请参阅 dm_exec_distributed_request_steps sys.databases 中的 step_index [&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md)。|  
|compute_node_id|**int**|此步骤表示的操作的类型。|请参阅 dm_exec_compute_nodes sys.databases 中的 compute_node_id [&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)。|  
|distribution_id|**int**|步骤的执行位置。|对于在节点范围内运行的请求，将设置为-1，而不是分布范围。|  
|状态|**nvarchar(32)**|此步骤的状态|活动、已取消、已完成、失败、排队|  
|error_id|**nvarchar （36）**|与此步骤关联的错误的唯一 id （如果有）|请参阅[dm_exec_compute_node_errors &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md)的 id，如果未发生错误，则为 NULL。|  
|start_time|**datetime**|步骤开始执行的时间|小于或等于当前时间，大于或等于此步骤所属的查询 end_compile_time。|  
|end_time|**datetime**|此步骤完成执行、已取消或失败的时间。|小于或等于当前时间，大于或等于 start_time，则将设置为 NULL 以查看当前正在执行或已排队的步骤。|  
|total_elapsed_time|**int**|执行查询步骤的总时间（毫秒）|介于0与 end_time 与 start_time 之间的差异。 对于排队步骤，为0。|  
|row_count|**bigint**|此请求更改或返回的总行数|0表示未更改或返回数据的步骤，否则为受影响的行数。 对于 DMS 步骤，将设置为-1。|  
|spid|**int**|执行查询分发的 SQL Server 实例上的会话 id||  
|command|nvarchar(4000)|保存此步骤的命令的完整文本。|步骤的任何有效请求字符串。 如果长度超过4000个字符，则截断。|  
  
## <a name="see-also"></a>另请参阅  
 [通过动态管理视图进行 PolyBase 故障排除](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [动态管理视图和函数 &#40;Transact-sql&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与数据库相关的动态管理视图 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
