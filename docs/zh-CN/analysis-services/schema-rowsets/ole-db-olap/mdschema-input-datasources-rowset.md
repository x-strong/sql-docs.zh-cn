---
title: MDSCHEMA_INPUT_DATASOURCES 行集 |Microsoft 文档
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MDSCHEMA_INPUT_DATASOURCES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_INPUT_DATASOURCES rowset
ms.assetid: 12482fd5-16e3-4171-9cb0-76d0d4f5308e
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e256ec44816db43f61c332a76942d27f63cb676b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="mdschemainputdatasources-rowset"></a>MDSCHEMA_INPUT_DATASOURCES 行集
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  介绍数据库中定义的数据源。  
  
## <a name="rowset-columns"></a>行集列  
 **MDSCHEMA_INPUT_DATASOURCES**行集包含以下各列。  
  
|列名|类型指示符|长度|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||此数据源所属目录的名称。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||不提供支持。|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**||数据源对象的名称。|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**||数据源的类型。 有效值包括：<br /><br /> **关系**<br /><br /> **Olap**|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**||创建数据源的日期。|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**||上次修改数据源的日期和时间。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||操作的用户友好说明。|  
|**超时**|**DBTYPE_UI4**||数据源的超时值。|  
  
 未对此架构行集进行排序。  
  
## <a name="restriction-columns"></a>限制列  
 **MDSCHEMA_INPUT_DATASOURCES**行集可限制在下表中列出的列。  
  
|列名|类型指示符|限制状态|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|選擇性。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|選擇性。|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**|選擇性。|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**|選擇性。|  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB for OLAP 架构行集](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  