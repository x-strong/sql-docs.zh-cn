---
title: 表中的计数行
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- totals [SQL Server], row counts
- row counts [SQL Server]
- column values [SQL Server]
- number of rows
- number of values
- counting rows
ms.assetid: dda4296a-1d16-4e77-8d6f-e295f6dd4e87
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 208705b0070ba60359f6fa0b6d543cdcf6ec55d3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254376"
---
# <a name="count-rows-in-a-table-visual-database-tools"></a>计算表中的行数 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
您可对表中的行进行计数以确定以下信息：  
  
-   表中的总行数，例如 `titles` 表中所有书籍的数量。  
  
-   表中满足特定条件的行数，例如， `titles` 表中某出版商出版的书籍数量。  
  
-   特定列中的值的数量。  
  
当对列中的值进行计数时，空值将不包含在计数中。 例如，假设要计算 `titles` 表中在 `advance` 列具有值的书籍的数量。 默认情况下，该计数包含所有值，而不仅仅是唯一值。  
  
以上所有三种类型的计数过程都是类似的。  
  
### <a name="to-count-all-the-rows-in-a-table"></a>对表中的所有行进行计数  
  
1.  确保您要汇总的表已经包含在“关系图”窗格中。  
  
2.  右键单击“关系图”窗格的背景，再从快捷菜单中选择“添加分组依据”  。 [查询和视图设计器](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md)会在“条件”窗格的网格中添加一个“分组依据”  列。  
  
3.  在表示表或表值对象的矩形中，选择“&#42; (所有列)”  。  
  
    查询和视图设计器会自动在“条件”窗格的“分组依据”列中填充 **Count** 一词，并为要汇总的列分配列别名。 您可以用更有意义的名称替换这一自动生成的别名。 有关详细信息，请参阅[创建列别名 (Visual Database Tools)](../../ssms/visual-db-tools/create-column-aliases-visual-database-tools.md)。  
  
4.  运行查询。  
  
### <a name="to-count-all-the-rows-that-meet-a-condition"></a>对满足条件的所有行进行计数  
  
1.  确保您要汇总的表已经包含在“关系图”窗格中。  
  
2.  右键单击“关系图”窗格的背景，再从快捷菜单中选择“添加分组依据”  。 查询和视图设计器会在“条件”窗格的网格中添加一个“分组依据”  列。  
  
3.  在表示表或表结构对象的矩形中，选择“&#42; (所有列)”  。  
  
    查询和视图设计器会自动在“条件”窗格的“分组依据”列中填充 **Count** 一词，并为要汇总的列分配列别名。 若要在查询输出中创建更实用的列标题，请参阅[创建列别名 (Visual Database Tools)](../../ssms/visual-db-tools/create-column-aliases-visual-database-tools.md)。  
  
4.  添加要搜索的数据列，再清除“输出”  列中的复选框。  
  
    查询和视图设计器会自动在网格的“分组依据”列中填充 **Group By** 一词。  
  
5.  将“分组依据”列中的 **Group By** 改为 **Where**。  
  
6.  在要搜索的数据列的“筛选器”  列中，输入搜索条件。  
  
7.  运行查询。  
  
### <a name="to-count-the-values-in-a-column"></a>对列中的值进行计数  
  
1.  确保您要汇总的表已经包含在“关系图”窗格中。  
  
2.  右键单击“关系图”窗格的背景，再从快捷菜单中选择“添加分组依据”  。 查询和视图设计器会在“条件”窗格的网格中添加一个“分组依据”  列。  
  
3.  将要计数的列添加到“条件”窗格中。  
  
    查询和视图设计器会自动在网格的“分组依据”列中填充 **Group By** 一词。  
  
4.  将“分组依据”列中的 **Group By** 改为 **Count**。  
  
    > [!NOTE]  
    > 若要只计算唯一值的数目，请选择 **Count Distinct**。  
  
5.  运行查询。  
  
## <a name="see-also"></a>另请参阅  
[对查询结果进行排序和分组 (Visual Database Tools)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[汇总查询结果 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
  
