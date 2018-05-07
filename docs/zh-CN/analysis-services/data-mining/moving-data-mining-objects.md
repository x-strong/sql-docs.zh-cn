---
title: 移动数据挖掘对象 |Microsoft 文档
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], models
- data mining editor [Analysis Services]
- mining models [Analysis Services], managing
- Data Mining Designer
- mining models [Analysis Services], modifying
ms.assetid: bc108407-2603-4387-b930-b5bb9df78069
caps.latest.revision: 45
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9d542908c4690e1f5fdf756ce5d3e030f914b3f8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="moving-data-mining-objects"></a>移动数据挖掘对象
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  移动数据挖掘对象的最常见情形是将模型从测试或分析环境部署到生产环境，或者与其他用户共享模型。  
  
 本主题介绍如何使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供的工具和脚本撰写语言来移动数据挖掘对象。  
  
## <a name="moving-data-mining-objects-between-databases-or-servers"></a>在数据库或服务器之间移动数据挖掘对象  
 您可以通过以下方法在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库之间或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例之间移动数据挖掘对象：  
  
-   将解决方案重新部署到其他数据库。  
  
-   撰写单独对象的脚本。  
  
-   备份然后还原分发数据库的副本。  
  
-   导出和导入结构和模型。  
  
 下一节更为详细地说明这些选项。  
  
### <a name="deploying"></a>部署  
 将解决方案部署到不同的服务器或数据库要求您具有以前通过使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]创建的解决方案文件。  
  
 有关部署 Analysis Services 解决方案的详细信息，请参阅[部署 Analysis Services 项目 (SSDT)](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)。  
  
### <a name="scripting"></a>脚本编写  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供可用于脚本对象的几种语言。  
  
-   **XMLA**：可以通过在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中右键单击对象，使用 XMLA 编写对象的脚本。 若要执行该脚本，请在目标服务器上的 **“XMLA 查询”** 窗口中打开该脚本。  
  
-   **DMX**：您可以通过使用模板或在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中提供的查询生成器之一创建脚本。  
  
 但请注意，在您可以使用各脚本撰写语言执行的任务之间存在差异：  
  
-   诸如对象说明和数据绑定之类的属性只能通过使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 语言创建或更改，使用 DMX 则不可以。  
  
-   只有 DMX 支持导入和导出挖掘对象。  
  
-   只有 DMX 支持生成 PMML 或从 PMML 导入模型定义。  
  
-   只有 DMX 支持使用应用程序数据对模型定型。 此外，DMX INSERT INTO 语句支持在不为键列提供值的情况下为模型定型。  
  
 有关详细信息，请参阅[使用 Analysis Services 脚本语言 (ASSL) 开发](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)。  
  
### <a name="backup-and-restore"></a>备份和还原  
 备份和还原整个 Analysis Services 数据库是在数据挖掘解决方案依赖于 OLAP 对象的情况下选择的方法。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]提供使更快、 更轻松的数据库备份的备份和还原功能。  
  
 有关备份的详细信息，请参阅 [备份和还原 Analysis Services 数据库](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)。  
  
### <a name="exporting-and-importing"></a>导出和导入  
 导出后再导入挖掘模型和结构（使用 DMX 语句）是最简单的移动或备份各关系数据挖掘对象的方法。 有关这些操作的 DMX 语法的详细信息，请参阅以下主题：  
  
-   [导出 & #40; DMX & #41;](../../dmx/export-dmx.md)  
  
-   [导入 & #40; DMX & #41;](../../dmx/import-dmx.md)  
  
 如果指定 INCLUDE DEPENDENCIES 选项，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 还将导出所有所需数据源视图的定义，并且将在导入模型或结构时在目标服务器上重新创建数据源视图。 完成了模型导入后，请确保对对象设置必需的挖掘权限。  
  
> [!NOTE]  
>  您不能使用 DMX 导出和导入 OLAP 模型。 如果挖掘模型基于 OLAP 多维数据集，则必须使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供的功能来备份和还原整个数据库，或者重新部署多维数据集及其模型。  
  
## <a name="see-also"></a>另请参阅  
 [数据挖掘解决方案和对象的管理](../../analysis-services/data-mining/management-of-data-mining-solutions-and-objects.md)  
  
  