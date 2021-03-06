---
title: 使用逻辑函数 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 723d481bc858d7d1db4a63cbb32ab5614eddbb55
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "68097174"
---
# <a name="using-logical-functions"></a>使用逻辑函数


  逻辑函数对对象和表达式执行逻辑操作或比较并返回布尔值。 在多维表达式 (MDX) 中，逻辑函数对确定成员的位置至关重要。  
  
 最常用的逻辑函数是**IsEmpty**函数。 有关如何使用**IsEmpty**函数的详细信息，请参阅使用[空值](../mdx/working-with-empty-values.md)。  
  
 下面的查询演示了如何使用**IsLeaf**和**IsAncestor**函数：  
  
 `WITH`  
  
 `//Returns true if the CurrentMember on Calendar is a leaf member, ie it has no children`  
  
 `MEMBER MEASURES.[IsLeafDemo] AS IsLeaf([Date].[Calendar].CurrentMember)`  
  
 `//Returns true if the CurrentMember on Calendar is an Ancestor of July 1st 2001`  
  
 `MEMBER MEASURES.[IsAncestorDemo] AS IsAncestor([Date].[Calendar].CurrentMember, [Date].[Calendar].[Date].&[1])`  
  
 `SELECT{MEASURES.[IsLeafDemo],MEASURES.[IsAncestorDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>另请参阅  
 [函数 &#40;MDX 语法&#41;](../mdx/functions-mdx-syntax.md)  
  
  
