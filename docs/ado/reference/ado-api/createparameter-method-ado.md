---
title: CreateParameter 方法（ADO） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords:
- CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 6cd78e3cbe992a3f2df5046a26eca990479cb3fd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760213"
---
# <a name="createparameter-method-ado"></a>CreateParameter 方法 (ADO)
创建具有指定属性的新[参数](../../../ado/reference/ado-api/parameter-object.md)对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>返回值  
 返回一个**参数**对象。  
  
#### <a name="parameters"></a>参数  
 *Name*  
 可选。 一个包含**参数**对象名称的**字符串**值。  
  
 *Type*  
 可选。 指定**参数**对象的数据类型的[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)值。  
  
 *方向*  
 可选。 指定**参数**对象类型的[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)值。  
  
 *Size*  
 可选。 一个**长整型**值，指定参数值的最大长度（以字符或字节为单位）。  
  
 值  
 可选。 一个**变量**，指定**参数**对象的值。  
  
## <a name="remarks"></a>备注  
 使用**CreateParameter**方法创建一个具有指定名称、类型、方向、大小和值的新**参数**对象。 您在参数中传递的任何值都将写入相应的**参数**属性。  
  
 此方法不会将**参数**对象自动追加到[Command](../../../ado/reference/ado-api/command-object-ado.md)对象的**Parameters**集合。 这使你可以设置其他属性，这些属性的值会在你将**参数**对象追加到集合时进行验证。  
  
 如果在*类型*参数中指定可变长度的数据类型，则必须在将其追加到**Parameters**集合之前传递*Size*参数或设置**参数**对象的[size](../../../ado/reference/ado-api/size-property-ado-parameter.md)属性;否则，将发生错误。  
  
 如果在*类型*参数中指定数值数据类型（**adNumeric**或**adDecimal**），则还必须设置[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)和[精度](../../../ado/reference/ado-api/precision-property-ado.md)属性。  
  
## <a name="applies-to"></a>应用于  
 [命令对象 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>另请参阅  
 [Append 和 CreateParameter 方法示例（VB）](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Append 和 CreateParameter 方法示例（VC + +）](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Append 方法（ADO）](../../../ado/reference/ado-api/append-method-ado.md)   
 [参数对象](../../../ado/reference/ado-api/parameter-object.md)   
 [参数集合 (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
