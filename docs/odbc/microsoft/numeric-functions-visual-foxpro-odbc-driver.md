---
title: 数值函数（Visual FoxPro ODBC 驱动程序） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3993a9a1b2412cb15229f2763c7c3b38f6b7862
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298157"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>数字函数（Visual FoxPro ODBC 驱动程序）
下表描述了 Visual FoxPro ODBC 驱动程序支持的 ODBC 数字函数;当同一个函数的 Visual FoxPro 语法与 ODBC 语法不同时，将列出等效的 Visual FoxPro。  
  
|ODBC 语法|Visual FoxPro 语法|  
|------------------|---------------------------|  
|ABS *（numeric_exp）*||  
|ACOS *（float_exp）*||  
|ASIN *（float_exp）*||  
|ATAN *（float_exp）*||  
|ATAN2 *（float_exp1，float_exp2）*|ATN2 （*float_exp1，float_exp2*）|  
|天花板 *（numeric_exp）*||  
|COS *（float_exp）*||  
|COT *（float_exp）*||  
|度 *（numeric_exp）*|RTOD *（numeric_exp）*|  
|EXP *（float_exp）*||  
|楼层 *（numeric_exp）*||  
|日志 *（float_exp）*||  
|LOG10 *（float_exp）*||  
|MOD *（integer_exp1，integer_exp2）*||  
|PI *（）*||  
|RADIANS *（numeric_exp）*|DTOR *（numeric_exp）*|  
|RAND *（[integer_exp]）*||  
|舍入 *（numeric_exp，integer_exp）*||  
|SIGN *（numeric_exp）*||  
|SIN *（float_exp）*||  
|SQRT *（float_exp）*||  
|TAN *（float_exp）*||  
  
 不支持以下数值函数：  
  
 POWER *（numeric_exp、integer_exp）*  
  
 截断 *（numeric_exp、integer_exp）*
