---
title: sys.databases （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- messages_TSQL
- sys.messages_TSQL
- sys.messages
- messages
dev_langs:
- TSQL
helpviewer_keywords:
- error messages [SQL Server]
- sys.messages catalog view
- error numbers [SQL Server]
ms.assetid: 8c16ecdf-68f4-4a2a-b594-086e3344e58a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6f54b68f7775910a7e25b858bd7579e751a75b98
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897135"
---
# <a name="messages-for-errors-catalog-views---sysmessages"></a>（错误）消息目录视图 - sys.messages
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  系统中的错误消息的每个**message_id**或**language_id**都包含一行，适用于系统定义消息和用户定义的消息。 有关详细信息，请参阅 [sp_addmessage (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)。  
   
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**message_id**|**int**|消息的 ID。 此 ID 在服务器中是唯一的。 编号在 50000 以下的消息 ID 是系统消息。|  
|**language_id**|**smallint**|用于**文本**的语言 ID，如**sys.syslanguages**中所定义。 这对于指定**message_id**是唯一的。|  
|severity |**tinyint**|消息的严重级别，在 1 到 25 之间。 这对于**message_id**中的所有消息语言都是相同的。|  
|**is_event_logged**|**bit**|1 = 出现错误时将消息记入事件日志。 这对于**message_id**中的所有消息语言都是相同的。|  
|**text**|**nvarchar(2048)**|对应的**language_id**处于活动状态时使用的消息文本。|  
  
## <a name="permissions"></a>权限  
 要求 **公共** 角色具有成员身份。 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 [THROW (Transact-SQL)](../../t-sql/language-elements/throw-transact-sql.md)   
 [Transact-sql&#41;的目录视图 &#40;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [消息 &#40;&#41; 目录视图的错误 &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)   
 [异常消息框编程](https://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)   
 [错误消息](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [数据库引擎事件和错误](../../relational-databases/errors-events/database-engine-events-and-errors.md)  
  
  
