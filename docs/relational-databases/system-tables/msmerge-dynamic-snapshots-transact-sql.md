---
title: MSmerge_dynamic_snapshots （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_dynamic_snapshots_TSQL
- MSmerge_dynamic_snapshots
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_dynamic_snapshots system table
ms.assetid: a5592b3c-731b-4fc9-ae4b-2602ed78248e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6e3c700e28ff105c6e99ebde9e7dbe8c4a82109a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889829"
---
# <a name="msmerge_dynamic_snapshots-transact-sql"></a>MSmerge_dynamic_snapshots (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSmerge_dynamic_snapshots**表跟踪为具有参数化行筛选器的合并发布定义的每个分区的筛选数据快照的位置。 该表存储在**发布**数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|合并分区的 ID。|  
|**dynamic_snapshot_location**|**nvarchar(255)**|分区的已筛选数据快照的位置。|  
|**last_updated**|**datetime**|已筛选数据快照刷新的日期。|  
  
## <a name="see-also"></a>另请参阅  
 [复制表 (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
