---
title: sys. database_filestream_options （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_filestream_options
- sys.database_filestream_options_TSQL
- database_filestream_options_TSQL
- sys.database_filestream_options
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_filestream_options catalog view
ms.assetid: 3383c607-0bbc-456a-ab37-7230f4cbf0e9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2cb185c2cec6bd2a7104384b3b75e14e2de4167f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85887936"
---
# <a name="sysdatabase_filestream_options-transact-sql"></a>sys.database_filestream_options (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  显示已启用的针对 FileTable 中的 FILESTREAM 数据的非事务性访问级别的相关信息。 为 SQL Server 实例中的每个数据库包含一行。  
  
 有关 FileTable 的详细信息，请参阅 [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)。  
  
  
|列|类型|说明|  
|------------|----------|-----------------|  
|**database_id**|**int**|数据库的 ID。 此值在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中是唯一的。|  
|**directory_name**|**nvarchar(255)**|所有 FileTable 命名空间的数据库级别目录。|  
|**non_transacted_access**|**tinyint**|已启用的针对 FILESTREAM 数据的非事务性访问的级别。 访问级别由**CREATE database**或**ALTER database**语句的 NON_TRANSACTED_ACCESS 选项设置。<br /><br /> 此设置具有以下值之一：<br /><br /> 0-未启用。 这是默认值。 通过为**NON_TRANSACTED_ACCESS**选项提供 " **OFF** " 值来设置此级别。<br /><br /> 1-只读访问。 通过提供**NON_TRANSACTED_ACCESS**选项**READ_ONLY**的值来设置此级别。<br /><br /> 3-完全访问权限。 通过为**NON_TRANSACTED_ACCESS**选项提供**FULL**值来设置此级别。<br /><br /> 5 - 正在转换到 READONLY<br /><br /> 6-正在转换为 OFF|  
|**non_transacted_access_desc**|**nvarchar(60)**|Non_transacted_access 中标识的非事务性访问级别的说明。<br /><br /> 此设置具有以下值之一：<br /><br /> 无-这是默认值。<br /><br /> READ_ONLY<br /><br /> FULL<br /><br /> IN_TRANSITION_TO_READ_ONLY<br /><br /> IN_TRANSITION_TO_OFF|  
  
## <a name="see-also"></a>另请参阅  
 [启用 FileTable 的先决条件](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
  
