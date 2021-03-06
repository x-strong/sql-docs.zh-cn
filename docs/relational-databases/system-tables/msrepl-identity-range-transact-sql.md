---
title: MSrepl_identity_range （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_identity_range_TSQL
- MSrepl_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_identity_range system table
ms.assetid: 6e92a8e8-7667-4c98-b1c4-46735bac50d8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4aafc6415d968d25b7ba4e708985e72378f9d95f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889511"
---
# <a name="msrepl_identity_range-transact-sql"></a>MSrepl_identity_range (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSrepl_identity_range**表提供标识范围管理支持。 该表存储在发布、分发和订阅数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|发布服务器的名称。|  
|**publisher_db**|**sysname**|发布数据库的名称。|  
|**tablename**|**sysname**|表的名称。|  
|**identity_support**|**int**|指定是否启用自动标识范围处理。 0 指定不启用自动标识范围处理。|  
|**next_seed**|**bigint**|如果启用自动标识范围，则指示下一个范围的起始点。|  
|**pub_range**|**bigint**|发布服务器标识范围大小。|  
|**range**|**bigint**|将分配到调整中订阅服务器的连续标识值的大小。|  
|**max_identity**|**bigint**|标识范围的最大边界。|  
|**threshold**|**int**|标识范围阈值百分比。|  
|**current_max**|**bigint**|可以分配但不是必须要分配的当前最大值。|  
  
## <a name="see-also"></a>另请参阅  
 [Transact-sql&#41;&#40;复制表](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
