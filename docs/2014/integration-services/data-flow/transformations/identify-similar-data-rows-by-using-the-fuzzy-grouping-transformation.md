---
title: 使用模糊分组转换标识相似数据行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Fuzzy Grouping transformation
- match similar data [Integration Services]
- similar data rows [Integration Services]
- fuzzy matches
ms.assetid: ffcb41a6-e23d-49ea-8c32-ac980e3dc495
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c860bad3b8453c58b1eb035b8d1f16db90b5a09c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85430584"
---
# <a name="identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation"></a>使用模糊分组转换标识相似数据行
  若要添加和配置模糊分组转换，包必须已包含至少一个数据流任务和一个源。  
  
### <a name="to-implement-fuzzy-grouping-transformation-in-a-data-flow"></a>在数据流中实现模糊分组转换  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目。  
  
2.  在解决方案资源管理器中，双击该包将其打开。  
  
3.  单击 **“数据流”** 选项卡，然后从 **“工具箱”** 中将模糊分组转换拖动到设计图面。  
  
4.  将连接线从数据源或前一个转换拖到模糊分组转换，从而将模糊分组转换连接到数据流。  
  
5.  双击模糊分组转换。  
  
6.  在 **“模糊分组转换编辑器”** 对话框中的 **“连接管理器”** 选项卡上，选择连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库的 OLE DB 连接管理器。  
  
    > [!NOTE]  
    >  转换要求连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库，以创建临时表和索引。  
  
7.  单击 **“列”** 选项卡，在 **“可用输入列”** 列表中，选中要使用的输入列的复选框，以标识数据集中的相似行。  
  
8.  选中 **“传递”** 列中的复选框，以标识要传递到转换输出的输入列。 在重复行的标识过程中不包含传递列。  
  
    > [!NOTE]  
    >  用于分组的输入列自动被选为传递列，所以当用于分组时无法取消选择这些输入列。  
  
9. 还可以更新 **“输出别名”** 列中的输出列名称。  
  
10. 还可以更新“组输出别名”  列中清除的列的名称。  
  
    > [!NOTE]  
    >  列的默认名称为输入列名称加“_clean”后缀。  
  
11. 还可以更新 **“匹配类型”** 列中所使用的匹配类型。  
  
    > [!NOTE]  
    >  至少有一列必须使用模糊匹配。  
  
12. 指定 **“最低相似性”** 列中的最低相似性级别列。 该值必须介于 0 和 1 之间。 值越接近 1，则输入列中的值必然越接近于组成一组。 最低相似性为 1，则指示完全匹配。  
  
13. 还可以更新 **“相似性输出别名”** 列中的相似性列的名称。  
  
14. 指定数据值中数字的处理方式，更新 **“数字”** 列中的值。  
  
15. 若要指定转换如何比较列中的字符串数据，请修改 **“比较标志”** 列中比较选项的默认选择。  
  
16. 单击“高级”  选项卡，修改该转换为唯一行标识符 (_key_in)、重复行标识符 (_key_out) 和相似性值 (_score) 添加到输出的列的名称。  
  
17. 还可以通过移动滑块来调节相似性阈值。  
  
18. 还可以清除标记分隔符复选框以忽略数据中的分隔符。  
  
19. 单击“确定”。   
  
20. 若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。  
  
## <a name="see-also"></a>另请参阅  
 [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md)   
 [Integration Services 转换](integration-services-transformations.md)   
 [Integration Services 路径](../integration-services-paths.md)   
 [数据流任务](../../control-flow/data-flow-task.md)  
  
  
