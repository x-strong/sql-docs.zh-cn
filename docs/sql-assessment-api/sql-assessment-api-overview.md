---
title: SQL Server 评估 API
description: 介绍什么是 SQL Server 评估 API。
ms.prod: sql
ms.technology: tools-other
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 11/04/2019
ms.openlocfilehash: 76a6e99d06061ae581b753ce0edd96a5a82d0f95
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "78946721"
---
# <a name="sql-assessment-api"></a>SQL 评估 API

SQL 评估 API 提供了一种评估 SQL Server 配置以获得最佳做法的机制。 该 API 附带一个规则集，其中包含 SQL Server 团队建议的最佳做法规则。 此规则集将随新版本的发布而进行强化，与此同时，构建此 API 的目的是提供高度可自定义和可扩展的解决方案。 这样用户便可以优化默认规则并创建自己的规则。

在确保 SQL Server 配置符合建议的最佳做法时，SQL 评估 API 非常有用。 初步评估后，可以通过定期安排评估来跟踪配置稳定性。

该 API 可用于评估 Azure SQL 数据库托管实例和 SQL Server 2012 及更高版本。 支持 Linux 上的 SQL。

## <a name="rules"></a>规则

规则（有时称为“检查”）在 JSON 格式的文件中进行定义。 规则集格式要求指定规则集名称和版本。 因此，当使用自定义规则集时，可以很容易地知道哪些建议来自哪些规则集。 

GitHub 上提供了 Microsoft 附带的规则集。 可以访问[示例存储库](https://aka.ms/sql-assessment-api)了解更多详细信息。

## <a name="sql-assessment-cmdlets-and-smo-extension"></a>SQL 评估 cmdlet 和 SMO 扩展

[SQL Server 管理对象 (SMO)](../relational-databases/server-management-objects-smo/installing-smo.md) 2019 年 7 月发行版和更高版本以及 [SQL Server PowerShell 模块](../powershell/download-sql-server-ps-module.md) 2019 年 7 月发行版和更高版本中均包含 SQL 评估 API。

* [安装 SMO](../relational-databases/server-management-objects-smo/installing-smo.md)

* [安装 SQL Server PowerShell 模块](../powershell/download-sql-server-ps-module.md)

SqlServer 模块提供两个新的 cmdlet 来与 SQL 评估 API 搭配使用：

* Get-SqlAssessmentItem - 提供 SQL Server 对象的可用评估检查列表 

* Invoke-SqlAssessment - 提供评估结果 

SQL 评估 API 扩展对 SMO Framework 进行补充，该扩展提供以下方法：

* GetAssessmentItems - 返回特定 SQL 对象的可用检查 (IEnumerable<…>)   

* GetAssessmentResults - 对评估进行同步评估并返回结果和错误（如果有）(IEnumerable<…>)   

* GetAssessmentResultsList - 对评估进行异步评估并返回结果和错误（如果有）(Task<…>) 

## <a name="get-started-using-sql-assessment-cmdlets"></a>开始使用 SQL 评估 cmdlet

针对所选的 SQL Server 对象执行评估。 默认规则集中仅提供针对两种对象的检查：Server 和 Database（除此之外，该 API 还支持另外两种对象：Filegroup 和 AvailabilityGroup）。 如果要评估 SQL 实例及其所有数据库，应分别为每个对象运行 SQL 评估 cmdlet。 或者，也可以将要评估的对象通过变量或管道传递给 SQL 评估 cmdlet。

SqlServer 和 RegisteredServer 对象是可交换的，因此可以将任何对象传递给 SQL 评估 cmdlet。

浏览下面的示例以开始使用。

1. 获取本地默认实例的可用检查列表，以便熟悉这些检查。 在此示例中，我们通过管道将 Get-SqlInstance cmdlet 的输出传递到 Get-SqlAssessmentItem cmdlet，以将实例对象传递给它。

    ```powershell
    Get-SqlInstance -ServerInstance 'localhost' | Get-SqlAssessmentItem
    ```

2. 获取实例的所有数据库的可用检查列表。 此处，我们使用 Get-Item cmdlet 和 Windows PowerShell SQL Server 提供程序实现的路径来获取数据库列表，然后将其传送到 Get-SqlDatabase cmdlet。

    ```powershell
    Get-Item SQLSERVER:\SQL\localhost\default | Get-SqlAssessmentItem
    ```

    此外，还可以使用 Get-SqlDatabase cmdlet 来执行相同的操作。

    ```powershell
    Get-SqlDatabase -ServerInstance 'localhost' | Get-SqlAssessmentItem
    ```

3. 获取实例的所有数据库的可用检查列表。 此处，我们使用 Get-Item cmdlet 和 Windows PowerShell SQL Server 提供程序实现的路径来获取数据库列表，然后将其传送到 Get-SqlDatabase cmdlet。

    ```powershell
    Get-Item SQLSERVER:\SQL\localhost\default | Get-SqlAssessmentItem
    ```

    此外，还可以使用 Get-SqlDatabase cmdlet 来执行相同的操作。

    ```powershell
    Get-SqlDatabase -ServerInstance 'localhost' | Get-SqlAssessmentItem
    ```

4. 调用实例的评估，并将结果保存到 SQL 表。 在此示例中，我们通过管道将 Get-SqlInstance cmdlet 的输出传递到 Invoke-SqlAssessment cmdlet，并通过管道将其结果传递给 Write-SqlTableData cmdlet。 在此示例中，Invoke-Assessment cmdlet 与 `-FlattenOutput` 参数一起运行。 此参数使输出适用于 Write-SqlTableData cmdlet。 如果不使用该参数，后者将引发错误。

    ```powershell
    Get-SqlInstance -ServerInstance 'localhost' |
    Invoke-SqlAssessment -FlattenOutput |
    Write-SqlTableData -ServerInstance 'localhost' -DatabaseName SQLAssessmentDemo -SchemaName Assessment -TableName Results -Force
    ```

    现在，我们来调用实例的所有数据库的评估，并将结果添加到同一个表中。

    ```powershell
    Get-SqlDatabase -ServerInstance 'localhost' |
    Invoke-SqlAssessment -FlattenOutput |
    Write-SqlTableData -ServerInstance 'localhost' -DatabaseName SQLAssessmentDemo -SchemaName Assessment -TableName Results -Force
    ```

5. 请按照表中的说明和链接来进一步了解建议。

6. 根据环境和组织要求自定义规则（见下文）。

7. 安排任务或作业以定期或按需运行评估从而衡量进度。

## <a name="customizing-rules"></a>自定义规则

规则是可自定义和可扩展的。 Microsoft 的规则集旨在适用于大多数环境。 但是，一个规则集不可能适用于所有环境。 用户可以编写自己的 JSON 文件并自定义现有规则或添加新规则。 [示例存储库](https://aka.ms/sql-assessment-api)中提供了自定义示例和完整的 Microsoft 发布的规则集。 有关如何使用自定义 JSON 文件运行 SQL 评估 cmdlet 的更多详细信息，请使用 Get-Help cmdlet。

### <a name="options-available-with-rule-customization-feature"></a>规则自定义功能提供的选项

#### <a name="enablingdisabling-certain-rules-or-groups-of-rules-using-tags"></a>启用/禁用某些规则或规则组（使用标签）

当特定规则不适用于环境时，或在完成计划工作以解决问题之后，可以使这些规则处于静默状态。

#### <a name="changing-threshold-parameters"></a>更改阈值参数

特定规则会将自身阈值与当前的指标值进行比较，以发现问题。 如果默认阈值不合适，可以对其进行更改。

#### <a name="adding-more-rules-written-by-you-or-third-parties"></a>添加更多由所在组织或第三方编写的规则

通过将一个或多个 JSON 文件作为参数添加到 SQL 评估 API 调用中，可以将多个规则集组合在一起。 组织可能会编写这些文件，或从第三方获取这些文件。 例如，可以让你的 JSON 文件禁用 Microsoft 规则集中的特定规则，让行业专家提供的另一个 JSON 文件包含你认为对环境有用的规则，然后再让另一个 JSON 文件更改该 JSON 文件中的某些阈值。

> [!IMPORTANT]  
> 我们强烈建议不要使用来自不受信任源的规则集，除非对其全面检查以确保它们安全。

## <a name="next-steps"></a>后续步骤

请参阅 [SQL Server 管理对象 (SMO)](../relational-databases/server-management-objects-smo/overview-smo.md) 和 [PowerShell](../powershell/download-sql-server-ps-module.md)。
