---
title: SQL-92 CAST 函数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09d2a2de710dafd4e744166c4219f4c903fd3321
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305058"
---
# <a name="sql-92-cast-function"></a>SQL-92 CAST 函数
在 SQL-92 中定义的**CAST**函数等效于在 ODBC 中定义的**转换**函数。 等效函数的语法如下所示：  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 SQL-92 **CAST**函数规定哪些数据类型可以转换为其他数据类型。 （有关详细信息，请参阅 SQL-92 规范。）FIPS 过渡级别支持**CAST**函数。  
  
 应用程序可以确定对**CAST**函数的支持，如下所示：  
  
1.  用 SQL_SQL_CONFORMANCE 信息类型调用**SQLGetInfo** 。 如果信息类型的返回值为 SQL_SC_FIPS127_2_TRANSITIONAL、SQL_SC_SQL92_INTERMEDIATE 或 SQL_SC_SQL92_FULL，则支持**CAST**函数。  
  
2.  如果 SQL_SQL_CONFORMANCE 信息类型的返回值为 SQL_SC_ENTRY_LEVEL 或0，则调用具有 SQL_SQL92_VALUE_EXPRESSIONS 信息类型的**SQLGetInfo** 。 如果设置了 SQL_SVE_CAST 位，则支持**CAST**函数。
