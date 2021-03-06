---
title: MSmerge_identity_range_allocations （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 72eb58276b78faf3ea3257cf56585b69c93b6e1a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889783"
---
# <a name="msmerge_identity_range_allocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  " **MSmerge_identity_range_allocations** " 表用于跟踪已发布项目的标识范围分配的历史记录，以及对发布服务器和订阅服务器的标识范围分配。 此表存储在分发数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|发布服务器的 ID。|  
|**publisher_db**|**nvarchar(128)**|发布数据库的名称。|  
|**发布**|**nvarchar(128)**|发布的名称。|  
|**文章**|**nvarchar(128)**|项目的名称。|  
|**订阅服务器**|**nvarchar(128)**|订阅服务器的名称。|  
|**subscriber_db**|**nvarchar(128)**|订阅数据库的名称。|  
|**is_pub_range**|**bit**|列出是否将标识范围分配给发布服务器。|  
|**ranges_allocated**|**tinyint**|已分配的标识范围数。|  
|**range_begin**|**numeric （38）**|范围的起始值。|  
|**range_end**|**numeric （38）**|范围中的最后一个值。|  
|**next_range_begin**|**numeric （38）**|要分配的下一个范围的起始值。|  
|**next_range_end**|**numeric （38）**|要分配的下一个范围中的最后一个值。|  
|**max_used**|**numeric （38）**|所使用的最大标识值。|  
|**time_of_allocation**|**datetime**|执行分配的时间。|  
  
## <a name="see-also"></a>另请参阅  
 [Transact-sql&#41;&#40;复制表](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
