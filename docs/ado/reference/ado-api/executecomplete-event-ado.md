---
title: ExecuteComplete 事件（ADO） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- ExecuteComplete event [ADO]
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
author: rothja
ms.author: jroth
ms.openlocfilehash: ae8b426a0e4b95498cb0d4f9a4590c3aaf30196d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760133"
---
# <a name="executecomplete-event-ado"></a>ExecuteComplete 事件 (ADO)
执行完命令后，将调用**ExecuteComplete**事件。  
  
## <a name="syntax"></a>语法  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>参数  
 *RecordsAffected*  
 指示受命令影响的记录数的**长整型**值。  
  
 *pError*  
 一个[错误](../../../ado/reference/ado-api/error-object.md)对象。 它描述了**adStatus**的值为**adStatusErrorsOccurred**时所发生的错误;否则，不会设置。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状态值。 当调用此事件时，如果导致事件的操作成功，则将此参数设置为**adStatusOK** ; 如果操作失败，则设置为**adStatusErrorsOccurred** 。  
  
 在此事件返回之前，将此参数设置为**adStatusUnwantedEvent**以防止后续通知。  
  
 *pCommand*  
 已执行的[命令](../../../ado/reference/ado-api/command-object-ado.md)对象。 包含一个**命令**对象，即使在调用的是**Execute**或 Recordset 时也是如此 **。打开**时无需显式创建**命令**，在这种情况下，将在 ADO 内部创建**命令**对象。  
  
 *pRecordset*  
 作为执行的命令的结果的[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象。 此**记录集**可能为空。 永远不应销毁此事件处理程序中的记录集对象。 如果 ADO 尝试访问不再存在的对象，则会导致访问冲突。  
  
 *pConnection*  
 [连接](../../../ado/reference/ado-api/connection-object-ado.md)对象。 执行操作时所用的连接。  
  
## <a name="remarks"></a>备注  
 由于连接的原因，可能会发生**ExecuteComplete**事件 **。**[执行](../../../ado/reference/ado-api/execute-method-ado-connection.md)、**命令。**[Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)、 **Recordset。**[打开](../../../ado/reference/ado-api/open-method-ado-recordset.md)，**记录集。**[Requery](../../../ado/reference/ado-api/requery-method.md)，或**记录集。**[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)方法。  
  
## <a name="see-also"></a>另请参阅  
 [ADO 事件模型示例（VC + +）](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO 事件处理程序摘要](../../../ado/guide/data/ado-event-handler-summary.md)
