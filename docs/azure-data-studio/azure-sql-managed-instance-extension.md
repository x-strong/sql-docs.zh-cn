---
title: Azure SQL 数据库托管实例扩展
titleSuffix: Azure Data Studio
description: 将 Azure Data Studio 与 Azure SQL 托管实例结合使用
ms.custom: seodec18
ms.date: 10/07/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: jovanpop-msft
ms.author: jovanpop
manager: alanyu
ms.openlocfilehash: 2269c594bd0fff036d4fe5d5d722aa5d78d4ca6d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2020
ms.locfileid: "75883998"
---
# <a name="azure-sql-database-managed-instance-dashboard-for-azure-data-studio-preview"></a>用于 Azure Data Studio 的 Azure SQL 数据库托管实例仪表板（预览版）

Azure SQL 数据库托管实例扩展提供一个仪表板，用于在 [Azure Data Studio](https://github.com/Microsoft/azuredatastudio) 中使用 [Azure SQL 数据库托管实例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index)。 此扩展提供以下功能：

- 显示托管实例属性，包括 vCore 和已用存储
- 监视前两小时的 CPU 和存储使用情况
- 显示配置警告和优化建议
- 显示数据库副本的状态
- 显示已筛选的错误日志

## <a name="install"></a>安装

可以安装此扩展的正式版本。 按照 [Azure Data Studio 文档](https://docs.microsoft.com/sql/azure-data-studio/extensions)中的步骤进行操作。
在“扩展”  窗格中，搜索“托管实例”并在此处安装它。 安装之后，会自动向你通知未来的任何扩展更新。

安装扩展后，会在 Azure Data Studio 中看到“托管实例”  选项卡。 在此处可以找到特定于托管实例的信息。

## <a name="properties"></a>属性

该扩展显示托管实例的技术特征和一些资源使用情况。

[ ![托管实例属性](media/azure-sql-mi-extension/ads-mi-tab1.png )](media/azure-sql-mi-extension/ads-mi-tab1.png#lightbox)

顶部窗格显示以下详细信息：

- **属性**。 获取有关托管实例的基本信息，包括可用 vCore、内存和存储。 还可找到当前服务层级、硬件代系和 IO 特征，例如实例日志写入吞吐量或文件 I/O 吞吐量特征。
- **本地 SSD 存储**。 在常规用途服务层级上，TempDB  文件存储在本地。 在业务关键服务层级上，所有  数据库文件都放置在本地 SSD 存储上。 在此部分中，可以查看托管实例使用的本地存储空间量。
- **Azure 高级磁盘存储**。 如果具有常规用途服务层级，则用户和系统数据库文件都会放置在 Azure 高级存储上。 在此部分中，可以查看使用的数据量、文件数和可用存储。 在业务关键服务层级上，此部分为空。
- **资源使用情况**。 查看托管实例在前两小时内使用的存储和 CPU 百分比。 这样便可以在实例大小接近限制时增加实例大小。

## <a name="recommendations"></a>建议

在“托管实例”  选项卡中选择第二个窗格时，会获得建议和警报，以帮助优化托管实例。

[ ![托管实例建议](media/azure-sql-mi-extension/ads-mi-tab2.png )](media/azure-sql-mi-extension/ads-mi-tab2.png#lightbox)

可能会看到以下一些建议：

- **即将达到存储空间限制**。 删除不必要的数据或增加实例存储大小。 达到存储限制的数据库可能无法处理均匀读取查询。
- **即将达到实例吞吐量限制**。 在负载接近以下服务层级限制时通知你：对于常规用途为 22 MB/s，对于业务关键为 48 MB/s。 请注意，托管实例会限制负载，以确保可以进行备份。
- **内存压力**。 低页生存期或大量 `PAGEIOLATCH` 等待统计信息可能表明实例正在从内存中退出页面，并不断尝试从磁盘加载更多页面。
- **日志文件限制**。 如果日志文件接近[常规用途服务层级上的文件 I/O 限制](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier)，则可能需要增大日志文件大小以获得更好的性能。
- **数据文件限制**。 如果数据文件接近[常规用途服务层级上的文件 I/O 限制](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier)，则可能需要增大文件大小以获得更好的性能。 此问题可能会导致内存压力并降低备份速度。
- **可用性问题**。 大量虚拟日志文件可能会影响性能。 如果发生进程故障，则此类问题可能会导致常规用途服务层级上的数据库恢复时间较长。

请定期查看这些建议，调查根本原因，并采取措施以纠正任何问题。 Azure SQL 数据库托管实例扩展提供了一些脚本，可以运行这些脚本来缓解报告的某些问题。

## <a name="replicas"></a>副本

“托管实例”  选项卡中的第三个窗格显示托管实例中的数据库副本状态。

[ ![托管实例副本](media/azure-sql-mi-extension/ads-mi-tab3.png )](media/azure-sql-mi-extension/ads-mi-tab3.png#lightbox)

在常规用途服务层级上，每个数据库都有单个（主要）副本。 在业务关键层级实例上，每个数据库都有一个主要副本和三个次要副本（其中一个用于只读工作负载）。 在“副本”  窗格上，可以监视同步过程，并验证是否所有次要副本都与主要副本同步。

## <a name="logs"></a>日志

“托管实例”  的第四个窗格显示最新的相关 SQL 错误日志条目。

[ ![托管实例日志条目](media/azure-sql-mi-extension/ads-mi-tab4.png )](media/azure-sql-mi-extension/ads-mi-tab4.png#lightbox)

虽然托管实例会生成大量日志条目，但是大多数日志条目是内部/系统信息。 此外，一些日志条目显示物理数据库名称（`GUID` 值），而不是实际逻辑数据库名称。

Azure SQL 数据库托管实例扩展会基于 [Dimitri Furman 方法](https://techcommunity.microsoft.com/t5/DataCAT/Azure-SQL-DB-Managed-Instance-sp-readmierrorlog/ba-p/305506)筛选出不必要的日志项。 该扩展还显示实际逻辑文件名，而不是物理名称。

## <a name="reporting-problems"></a>报告问题

如果 Azure SQL 数据库托管实例扩展遇到任何问题，请转到[扩展 GitHub 项目](https://github.com/JocaPC/AzureDataStudio-Managed-Instance/issues)并报告问题。

## <a name="code-of-conduct"></a>行为准则

此项目采用了 [Microsoft 开放源代码行为准则][conduct-code]。

有关详细信息，请参阅[行为准则常见问题解答][conduct-FAQ]，如有任何其他问题或评论，请联系 [opencode@microsoft.com][conduct-email]。

## <a name="next-steps"></a>后续步骤

有关详细信息，请访问 [GitHub 项目](https://github.com/JocaPC/AzureDataStudio-Managed-Instance/)。

[conduct-code]: https://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: https://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
