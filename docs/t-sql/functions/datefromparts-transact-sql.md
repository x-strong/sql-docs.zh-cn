---
title: DATEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATEFROMPARTS_TSQL
- DATEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATEFROMPARTS function
ms.assetid: 5b885376-87aa-41f1-9e18-04987aead250
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a84fe60979d460030248ca9de912cd9d0b9d9acc
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823215"
---
# <a name="datefromparts-transact-sql"></a>DATEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

此函数返回映射到指定年、月、日值的 date 值  。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
DATEFROMPARTS ( year, month, day )  
```  
  
## <a name="arguments"></a>参数  
*year*  
指定年份的整数表达式。
  
month   
指定月份（从1 到12）的整数表达式。
  
day   
指定日期的整数表达式。
  
## <a name="return-types"></a>返回类型
**date**
  
## <a name="remarks"></a>备注  
`DATEFROMPARTS` 返回一个 date 值，其中日期部分设置为指定的年、月和日，时间部分设置为默认值  。 对于无效参数，`DATEFROMPARTS` 将引发错误。 如果至少有一个必需参数具有 NULL 值，则 `DATEFROMPARTS` 返回 NULL。
  
此函数可在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更高版本的服务器上执行远程处理。 它不能无法在版本低于 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 的服务器上执行远程处理。
  
## <a name="examples"></a>示例  
此示例演示了操作中的 `DATEFROMPARTS` 函数。
  
```sql
SELECT DATEFROMPARTS ( 2010, 12, 31 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
----------------------------------  
2010-12-31  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>另请参阅
[date (Transact-SQL)](../../t-sql/data-types/date-transact-sql.md)
  
  

