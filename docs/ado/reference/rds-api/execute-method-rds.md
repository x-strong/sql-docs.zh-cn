---
title: Execute 方法（RDS） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 2d9c30e9-ab5b-4920-91b8-48454c2fb5d8
author: rothja
ms.author: jroth
ms.openlocfilehash: b4c44e48c46abab1cc15e3fbf90592414fad7c9c
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "82752678"
---
# <a name="execute-method-rds"></a>Execute 方法 (RDS)
执行请求并创建 ADO 记录集，以便在 ADO 2.5 和更高版本中使用。  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，Windows 操作系统中不再包含 RDS 服务器组件（有关详细信息，请参阅 Windows 8 和[Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416)）。 在 Windows 的未来版本中将删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.Execute(ConnectionString As String, HandlerString As String, QueryString As String, lFetchOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters, [lcid As Long], [pInformation])  
```  
  
#### <a name="parameters"></a>参数  
 *ConnectionString*  
 一个字符串，用于连接到将发送请求以执行的 OLE DB 提供程序。 如果使用*HandlerString*指定处理程序，则它可以编辑或替换连接字符串。  
  
 *HandlerString*  
 一个由两部分组成的字符串，用于标识要与此执行一起使用的处理程序。 该字符串包含两个部分。 第一部分包含要使用的处理程序的名称（ProgID）。 第二部分包含要传递到处理程序的参数。 如何解释参数字符串的详细信息特定于每个处理程序。 这两个部分由字符串中逗号的第一个实例分隔。 参数字符串可以包含其他逗号。 这些参数是可选的。  
  
 *QueryString*  
 在连接字符串中标识的 OLE DB 提供程序支持的命令语言中的命令。 对于基于 SQL 的访问接口，*查询字符串*可能包含 transact-sql 命令语句，但对于非 SQL 提供程序（例如，MSDataShape），这可能不是 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询语句。  
  
 如果正在使用处理程序，则该处理程序可以更改或替换此处指定的值。 例如，处理程序通常将*QueryString*替换为其 .ini 文件中的查询字符串。 默认情况下，使用 Msdfmap 文件。  
  
 *lFetchOptions*  
 指示异步提取的类型。  
  
 有关详细信息，请参阅[FetchOptions 属性（RDS）](../../../ado/reference/rds-api/fetchoptions-property-rds.md)。  
  
 *TableID*  
 VT_EMPTY 或 VT_BSTR 类型的**变体**。 如果此值为 VT_EMPTY 类型，则将忽略此值。 如果它的类型为 VT_BSTR，则将使用**adCmdTableDirect**创建该记录集，并使用此处指定的值并忽略*QueryString*参数。  
  
 *lExecuteOptions*  
 执行选项的位掩码：  
  
 1 =*ReadOnly*将使用**adLockReadOnly**打开记录集。  
  
 2 =*NoBatch*将使用**adLockOptimistic**打开记录集。  
  
 4 =*AllParamInfoSupplied*调用方保证在*pParameters*中提供所有参数的参数信息。  
  
 8 = 将从 OLE DB 提供程序获取查询的*GetInfo*参数信息，并在*pParameters*参数中返回该信息。 查询不会执行，并且不会返回任何记录集。  
  
 16 =*GetHiddenColumns*将使用**adLockBatchOptimistic**打开记录集，任何隐藏的列都将包含在记录集中。  
  
 *ReadOnly*、 *NoBatch*和*GetHiddenColumns*是互斥的选项;但是，它不会生成错误来设置其中的多个错误。 如果设置了多个选项， *GetHiddenColumns*将优先于所有其他选项，然后使用*ReadOnly*。 如果未指定任何选项，则默认情况下，将使用**adLockBatchOptimistic**打开记录集，且不会在记录集中包含隐藏的列。  
  
 *pParameters*  
 一个包含参数定义的安全数组的**变体**。 如果在*lExecuteOptions*中指定了*GetInfo*选项，则此参数用于返回从 OLE DB 提供程序获取的参数定义。 否则，此参数可以为空。  
  
 *lcid*  
 LCID，用于生成在*pInformation*中返回的任何错误。  
  
 *pInformation*  
 一个指针，指向执行返回的信息错误。 如果为 NULL，则不返回错误信息。  
  
## <a name="remarks"></a>备注  
 *HandlerString*参数可以为 null。 在这种情况下会发生什么情况取决于 RDS 服务器的配置方式。 "MSDFMAP" 的处理程序字符串指示应使用 Microsoft 提供的处理程序（Msdfmap）。 "MASDFMAP" 的处理程序字符串指示应使用 Msdfmap 处理程序，并且应将参数 "sample" 传递到处理程序中，。 MSDFMAP 会将参数解释为使用 schema.ini 检查连接和查询字符串的方向。  
  
## <a name="applies-to"></a>应用于  
 [DataFactory 对象 (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


