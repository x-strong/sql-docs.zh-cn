---
title: sys.sys注释（Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syscomments_TSQL
- syscomments
- syscomments_TSQL
- sys.syscomments
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syscomments compatibility view
- syscomments system table
ms.assetid: 767dd410-6bc9-4c4a-ab0f-6d2cf6163426
author: rothja
ms.author: jroth
ms.openlocfilehash: 49473b85d6c0a52f9c7ec7ed4bab519b19b04693
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883483"
---
# <a name="syssyscomments-transact-sql"></a>sys.syscomments (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  包含数据库中的每个视图、规则、默认值、触发器、CHECK 约束、DEFAULT 约束和存储过程的条目。 **Text**列包含原始 SQL 定义语句。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 我们建议您改用 sys.sql_modules。 有关详细信息，请参阅[sys.databases&#41;sql_modules &#40;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|该文本适用的对象 ID。|  
|**数字**|**smallint**|如果进行分组，则为过程分组内的号码。<br /><br /> 0 = 项不是过程。|  
|**colid**|**smallint**|超过 4,000 个字符的对象定义的行序列号。|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**ctext**|varbinary(8000)****|SQL 定义语句的原始字节。|  
|**texttype**|**smallint**|0 = 用户提供的注释<br /><br /> 1 = 系统提供的注释<br /><br /> 4 = 加密的注释|  
|language|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**过**|**bit**|指示过程定义是否已经过模糊处理。<br /><br /> 0 = 未经模糊处理<br /><br /> 1 = 已经模糊处理<br /><br /> ** \* \* 重要 \* 说明 \* **若要对存储过程定义进行模糊处理，请使用带有 ENCRYPTION 关键字的 CREATE procedure。|  
|**压缩**|**bit**|始终返回 0。 这表明过程已压缩。|  
|**text**|**nvarchar(4000)**|SQL 定义语句的实际文本。<br /><br /> 解码后的表达式的语义等同于原始文本，但是没有语法保证。 例如，解码后的表达式中删除了空格。<br /><br /> 此 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 兼容视图从当前结构中获取信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，并且可以返回比**nvarchar （4000）** 定义更多的字符。 **sp_help**返回**nvarchar （4000）** 作为文本列的数据类型。 使用**syscomments**时，请考虑使用**nvarchar （max）**。 对于新的开发工作，请勿使用**syscomments**。|  
  
## <a name="see-also"></a>另请参阅  
 [将系统表映射到系统视图 &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [兼容性视图 (Transact SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
