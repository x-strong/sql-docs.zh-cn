---
title: 替换模板参数
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b0c4cc26fddff13e388b74593aa9d8f9331359f8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "75245679"
---
# <a name="replace-template-parameters"></a>替换模板参数
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
模板包含每次使用模板时可由实现特定值替换的参数。 在代码编辑器中打开模板之后，可以使用与您的实现相关的值替换这些参数。  
  
## <a name="before-you-begin"></a>开始之前  
“指定模板参数的值”  对话框是包含三列的网格。 “参数”  和“类型”  列是只读的，不能更改。 查看“值”  列的内容，将任意默认值更改为对你的实现合适的值。  
  
若要使用此对话框，必须将脚本中的参数按以下格式括在尖括号 (`< >`) 内：`<`parameter_name  `,` data_type  `,` default_value  `>`。  
  
## <a name="replace-template-parameters"></a>替换模板参数  
在代码编辑器窗口中打开模板后：  
  
1.  在 **“查询”** 菜单上，单击 **“指定模板参数的值”** 。  
  
2.  在“指定模板参数的值”  对话框中，“值”  列包含每个参数的建议值。 接受值或将其替换为新值。  
  
3.  单击“确定”  关闭“替换模板参数”  对话框并在查询编辑器中修改脚本。  
  
## <a name="see-also"></a>另请参阅  
[模板资源管理器](../../ssms/template/template-explorer.md)  
[打开模板](../../ssms/template/open-a-template.md)  
  
