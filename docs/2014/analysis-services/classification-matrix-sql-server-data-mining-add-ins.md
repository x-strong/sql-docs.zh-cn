---
title: 分类矩阵（SQL Server 数据挖掘外接程序） |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- classification matrix
- confusion table
- mining models, testing
ms.assetid: d6f620f4-39af-4714-9628-28ce3c361fca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8af87605bb8c4c2cf4bcd53cce3f7ab0019b7d94
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527513"
---
# <a name="classification-matrix-sql-server-data-mining-add-ins"></a>分类矩阵（SQL Server 数据挖掘外接程序）
  ![“数据挖掘”功能区中的“分类矩阵”按钮](media/dmc-cmatrix.gif "“数据挖掘”功能区中的“分类矩阵”按钮")  
  
 可以使用分类矩阵评估模型进行预测的准确性。 若要生成分类矩阵，您可通过模型运行测试数据集，分类矩阵工具会将来自测试集的实际值与模型进行的预测进行比较。 通过查看该矩阵，您可以一目了然地判断模型正确的频率以及预测错误的频率。  
  
 在这些外接程序中，使用**分类矩阵**向导选择模型，指定测试数据，然后生成结果矩阵。  
  
## <a name="how-to-read-a-classification-matrix"></a>如何读取分类矩阵  
 假设您的目标是设计客户忠实度计划，然后将客户分配到适当的类别，以便您可以向他们提供适当的激励级别。 您已经实现了三个级别的奖励计划--青铜、银和黄金，并在试用阶段向客户提供这些级别。 您还设计了一个模型，该模型分析客户并预测正确的类别。 现在，您将对试用数据使用分类矩阵以确定模型在为所有客户预测正确类别方面的表现。  
  
 来自分类矩阵的表可告知您基于模型分配给每种类别的客户数，并将该结果与实际针对每种奖励级别注册的客户数进行比较。  
  
||铜卡（实际数）|金卡（实际数）|银卡（实际数）|  
|-|-----------------------|---------------------|-----------------------|  
|铜卡|**94.45%**|15.18%|1.70%|  
|Gold|2.72%|**84.82%**|0.00%|  
|Silver|1.84%|0.00%|**93.80%**|  
|*恰当*|*95.45%*|*84.82%*|*98.30%*|  
|*分类错误*|*4.55%*|*15.18%*|*1.70%*|  
  
-   每列显示测试数据集中的实际值。  
  
-   每行显示预测值。  
  
-   从矩阵的左上角到右下角沿对角线排列的粗体值显示了模型预测的正确情况。  
  
-   对角线之外的所有其他值都表示错误。 一些错误是假正，表示模型预测客户会加入金牌计划，但事实并非如此。  根据您的具体业务领域，误报成本可能非常高昂。  
  
     有些错误是假负，表示模型预测客户应无意加入某计划，但客户实际却加入了该计划。 根据具体工作领域，这种丧失机会的成本也可能十分高昂。  
  
## <a name="using-the-classification-matrix-wizard"></a>使用分类矩阵向导  
  
1.  选择预测要基于的挖掘模型。  
  
2.  选择新测试数据的源，或使用随结构保存的测试数据。  
  
3.  选择要评估其准确性的列。 可以在创建矩阵时仅选择一列，但是该列可以具有多个值。  
  
     提示：如果可预测列要与许多列比较，则分类矩阵可能难以解读。  
  
     在 "**选择要预测的列**" 页中，还可以指定是否要显示错误和不正确的值的计数，或显示百分比。  
  
4.  在“选择源数据”页上，指示是使用外部测试数据还是随模型保存的测试数据。  
  
5.  如果使用外部测试数据，则需要在向导的 "**指定关系**" 页上将模型映射到输入列。  
  
     如果使用嵌入式测试数据集，则会为您自动执行映射  
  
6.  单击 "**完成**" 可对模型运行预测并生成分类矩阵。  
  
     该向导将创建一个报表，报表中包含分类矩阵和有关分析的其他详细信息。 此报表保存为 Excel 中的表，报表上方有一个摘要，指示正确预测的事例数以及错误的预测数。  
  
### <a name="requirements"></a>要求  
  
-   若要创建分类矩阵，您必须拥有支持准确性度量的现有挖掘模型的访问权限。 预测模型和关联模型无法使用此工具进行度量。  
  
-   所度量的模型需要预测作为离散值或已离散化的值。  
  
-   如果未使用选项来保存测试集以及结构或模型，则需要获取一个输入数据集，该数据集本质上具有与在模型中使用的列数相同的列。  
  
-   数据挖掘模型和测试中要使用的新数据都必须包含至少一个可预测的列，而且这些列必须包含同类数据。  
  
### <a name="known-issues"></a>已知问题  
 在 SQL Server 2012 和 SQL Server 2014 中，将内部测试数据集映射到模型的功能在**分类矩阵**工具中不起作用。 但是，您可以指定外部数据集，然后选择定型集作为输入以确定原始数据集上的错误。  
  
## <a name="see-also"></a>另请参阅  
 [验证模型和使用模型进行预测 &#40;Excel 数据挖掘外接程序&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [浏览数据挖掘外接 &#40;SQL Server 数据&#41;](explore-data-sql-server-data-mining-add-ins.md)   
 [检测类别 &#40;Excel&#41;的表分析工具](detect-categories-table-analysis-tools-for-excel.md)  
  
  
