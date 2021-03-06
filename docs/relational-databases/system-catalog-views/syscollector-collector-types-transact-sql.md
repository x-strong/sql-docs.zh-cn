---
title: syscollector_collector_types （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_collector_types
- syscollector_collector_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_collector_types view
ms.assetid: d5cd30bb-89fd-4814-a7e8-9074f043f90f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d1ff2329d0070d554f87e405a6030b744e98d23a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896751"
---
# <a name="syscollector_collector_types-transact-sql"></a>syscollector_collector_types (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  提供有关收集项的收集器类型的信息。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**collector_type_uid**|**uniqueidentifer**|收集类型的 GUID。 不可为 null。|  
|name|**sysname**|收集类型的名称。 不可为 null。|  
|**parameter_schema**|**xml**|描述指定收集器类型的配置情况的 XML 架构。 此 XML 架构用于验证与特定收集项实例相关联的实际 XML 配置。 可以为 Null。|  
|**parameter_formatter**|**xml**|确定用于转换 XML 的模板，以便在收集组属性页中使用。 可以为 Null。|  
|**collection_package_id**|**uniqueidentifer**|收集包的 GUID。 不可为 null。|  
|**collection_package_path**|**nvarchar(4000)**|提供收集包的路径。 可以为 Null。|  
|**collection_package_name**|**sysname**|收集包的名称。 不可为 null。|  
|**upload_package_id**|**uniqueidentifer**|上载包的 GUID。 不可为 null。|  
|**upload_package_path**|**nvarchar(4000)**|提供上载包的路径。 可以为 Null。|  
|**upload_package_name**|**sysname**|上载包的名称。 不可为 null。|  
|**is_system**|**bit**|打开（1）或关闭（0）以指示收集器类型是否随数据收集器一起提供，或者是否在**dc_admin**稍后添加了它。 这可以是内部开发的或由第三方开发的自定义类型。 不可为 null。|  
  
## <a name="permissions"></a>权限  
 需要**dc_operator** **dc_proxy**选择。  
  
## <a name="change-history"></a>更改历史记录  
  
|更新的内容|  
|---------------------|  
|已更新**collection_type_uid**列名称以**collector_type_uid**。|  
|更正了**parameter_schema**列的说明以指示该值可以为 null。|  
|添加了**parameter_formatter**列。|  
|更正了**collection_package_path**列的数据类型，并更新了说明以指示该值可以为 null。|  
|更正了**upload_package_path**列的数据类型，并更新了说明以指示该值可以为 null。|  
  
## <a name="see-also"></a>另请参阅  
 [&#40;Transact-sql&#41;的数据收集器存储过程](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [&#40;Transact-sql&#41;的数据收集器视图](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [数据收集](../../relational-databases/data-collection/data-collection.md)  
  
  
