---
title: ActiveConnection 属性（ADO MD） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActiveConnection
- Cellset::ActiveConnection
- Catalog::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO MD]
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
author: rothja
ms.author: jroth
ms.openlocfilehash: 13a24320f7b49d8d2a0e1341bff2d9a4cca575dd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765308"
---
# <a name="activeconnection-property-ado-md"></a>ActiveConnection 属性 (ADO MD)
指示当前单元集或目录当前属于哪个 ADO[连接](../../../ado/reference/ado-api/connection-object-ado.md)对象。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回一个**变量**，该变量包含定义连接或**连接**对象的字符串。 默认值为空。  
  
## <a name="remarks"></a>备注  
 可将此属性设置为有效的 ADO**连接**对象或有效的连接字符串。 如果将此属性设置为连接字符串，则提供程序将使用此定义创建新的**连接**对象，并打开连接。  
  
 如果使用[open](../../../ado/reference/ado-md-api/open-method-ado-md.md)方法的*ActiveConnection*参数打开[单元集](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)对象，则**ActiveConnection**属性将继承参数的值。  
  
 将[目录](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)对象的**ActiveConnection**属性设置为 "**无**" 可释放关联的数据，包括[CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)集合中的数据以及任何相关的[维度](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)、[层次结构](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)、[级别](../../../ado/reference/ado-md-api/level-object-ado-md.md)和[成员](../../../ado/reference/ado-md-api/member-object-ado-md.md)对象。 关闭用于打开**目录**的**连接**对象具有与将**ActiveConnection**属性设置为**Nothing**相同的效果。  
  
 更改**目录**对象的**ActiveConnection**属性所引用的连接的默认数据库将会使该**目录**的内容失效。  
  
 如果尝试更改打开的**单元集**对象的**ActiveConnection**属性，则会发生错误。  
  
> [!NOTE]
>  在 Visual Basic 中，在将**ActiveConnection**属性设置为**连接**对象时，请记住使用**Set**关键字。 如果省略**Set**关键字，则实际上是将**ActiveConnection**属性设置为与**连接**对象的默认属性**ConnectionString**相等。 代码将正常运行;但是，你将创建一个与数据源的其他连接，这可能会对性能产生负面影响。  
  
 使用 MSOLAP 数据访问接口时，将连接字符串中的数据源设置为服务器名称，并将初始目录设置为数据源中目录的名称。 若要连接到与服务器断开连接的多维数据集文件，请将该位置设置为的完整路径。.CUB 文件。 在任一情况下，请将提供程序设置为提供程序名称。 例如，以下字符串使用 MSOLAP 提供程序连接到名为**Servername**的服务器上名为 Bobs-sfpreviewcluster Video Store 的目录：  
  
```  
"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"  
```  
  
 以下字符串连接到位于 C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub 位置的本地多维数据集文件：  
  
```  
"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"  
```  
  
## <a name="applies-to"></a>应用于  
  
|||  
|-|-|  
|[目录对象 (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[单元集对象 (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|  
  
## <a name="see-also"></a>另请参阅  
 [单元集示例（VB）](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Connection 对象（ADO）](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Open 方法 (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
