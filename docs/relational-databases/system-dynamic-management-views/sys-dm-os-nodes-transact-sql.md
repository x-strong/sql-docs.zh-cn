---
title: sys. dm_os_nodes （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 02/13/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_nodes
- dm_os_nodes_TSQL
- dm_os_nodes
- sys.dm_os_nodes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_nodes dynamic management view
ms.assetid: c768b67c-82a4-47f5-850b-0ea282358d50
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dfbb10c989300f33a551cb4686e7467eaf90a604
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754044"
---
# <a name="sysdm_os_nodes-transact-sql"></a>sys.dm_os_nodes (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asdw-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

一个名为 SQLOS 的内部组件可创建模拟硬件处理器位置的节点结构。 可以通过使用[软件 NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md)来更改这些结构，以创建自定义节点布局。  

> [!NOTE]
> 从开始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 将自动对某些硬件配置使用软件 NUMA。 有关详细信息，请参阅[自动软件 NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md#automatic-soft-numa)。
  
下表提供了有关这些节点的信息。  
  
> [!NOTE]
> 若要从或调用此 DMV [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ，请使用名称**dm_pdw_nodes_os_nodes**。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|node_id|**smallint**|节点的 ID。|  
|node_state_desc|**nvarchar(256)**|对节点状态的说明。 首先显示互斥的值，后跟可组合的值。 例如：<br /> Online, Thread Resources Low, Lazy Preemptive<br /><br />有四个互斥 node_state_desc 值。 下面列出了这些说明。<br /><ul><li>联机：节点处于联机状态<li>脱机：节点处于脱机状态<li>空闲：节点没有挂起的工作请求，已进入空闲状态。<li>IDLE_READY：节点没有挂起的工作请求，已准备好进入空闲状态。</li></ul><br />下面列出了三个可组合的 node_state_desc 值及其说明。<br /><ul><li>DAC：此节点保留用于[专用管理连接](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)。<li>THREAD_RESOURCES_LOW：由于内存不足，无法在此节点上创建新线程。<li>热添加：指示添加节点以响应热添加 CPU 事件。</li></ul>|  
|memory_object_address|**varbinary(8)**|与此节点关联的内存对象的地址。 一对一关系与[sys. dm_os_memory_objects](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)memory_object_address。|  
|memory_clerk_address|**varbinary(8)**|与此节点关联的内存分配器的地址。 一对一关系与[sys. dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)memory_clerk_address。|  
|io_completion_worker_address|**varbinary(8)**|分配给此节点的 IO 完成的工作线程的地址。 一对一关系与[sys. dm_os_workers](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)worker_address。|  
|memory_node_id|**smallint**|此节点所属的内存节点的 ID。 与[sys. dm_os_memory_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-nodes-transact-sql.md)memory_node_id 的多对一关系。|  
|cpu_affinity_mask|**bigint**|用于标识此节点所关联的 CPU 的位图。|  
|online_scheduler_count|**smallint**|此节点管理的联机计划程序的数目。|  
|idle_scheduler_count|**smallint**|没有活动的工作线程的联机计划程序数目。|  
|active_worker_count|**int**|在此节点所管理的所有计划程序上处于活动状态的工作线程数目。|  
|avg_load_balance|**int**|此节点上每个计划程序的平均任务数。|  
|timer_task_affinity_mask|**bigint**|用于标识可为其分配计时器任务的计划程序的位图。|  
|permanent_task_affinity_mask|**bigint**|用于标识可为其分配永久性任务的计划程序的位图。|  
|resource_monitor_state|**bit**|每个节点都分配有一个资源监视器。 资源监视器可以处于运行或空闲状态。 值 1 表示正在运行，值 0 表示处于空闲状态。|  
|online_scheduler_mask|**bigint**|标识此节点的进程关联掩码。|  
|processor_group|**smallint**|标识此节点的处理器组。|  
|cpu_count |**int** |此节点可用的 Cpu 数。 |
|pdw_node_id|**int**|此分发所在的节点的标识符。<br /><br /> **适用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>权限

在上 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ，需要 `VIEW SERVER STATE` 权限。   
在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 高级层上，需要具有 `VIEW DATABASE STATE` 数据库中的权限。 在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 标准层和基本层上，需要**服务器管理员**或**Azure Active Directory 管理员**帐户。   

## <a name="see-also"></a>另请参阅    
 [&#40;Transact-sql 的与操作系统相关的动态管理视图 SQL Server&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [Soft-NUMA (SQL Server)](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
