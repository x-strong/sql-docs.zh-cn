---
title: CEILING（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ed1cf4d70dc1e04f2419070b3672522833524c6
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85429014"
---
# <a name="ceiling-ssis-expression"></a>CEILING（SSIS 表达式）
  返回大于或等于数值表达式的最小整数。  
  
## <a name="syntax"></a>语法  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>参数  
 *numeric_expression*  
 有效的数值表达式。  
  
## <a name="result-types"></a>结果类型  
 提交给函数的数值表达式的数据类型。  
  
## <a name="remarks"></a>备注  
 如果参数为空，则 CEILING 返回的结果为空。  
  
## <a name="expression-examples"></a>表达式示例  
 这些示例对正值、负值和零值应用 CEILING 函数。  
  
```  
CEILING(123.74)  
```  
  
 返回 124.00  
  
```  
CEILING(-124.27)  
```  
  
 返回 -124.00  
  
```  
CEILING(0.00)  
```  
  
 返回 0.00  
  
## <a name="see-also"></a>另请参阅  
 [FLOOR（SSIS 表达式）](floor-ssis-expression.md)   
 [函数（SSIS 表达式）](functions-ssis-expression.md)  
  
  
