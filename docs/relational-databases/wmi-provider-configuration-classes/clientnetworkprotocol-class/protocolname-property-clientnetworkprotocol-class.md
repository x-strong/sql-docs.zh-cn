---
title: ProtocolName 属性（ClientNetworkProtocol）
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolName Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolName property
ms.assetid: f8527121-fbcd-4d30-9b4a-1461149cb5a8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 17236b165dd76fa2713a9fed99e4fd3df58a6097
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85888988"
---
# <a name="protocolname-property-clientnetworkprotocol-class"></a>ProtocolName 属性（ClientNetworkProtocol 类）
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  获取[配置客户端协议](https://technet.microsoft.com/library/ms181035.aspx)指定的当前网络协议的名称。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.ProtocolName [= value]  
```  
  
## <a name="parts"></a>组成部分  
 *object*  
 一个表示客户端使用的网络协议的[ClientNetworkProtocol 类](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md)对象 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 一个字符串值，该值指定[SetOrderValue 方法（ClientNetworkProtocol 类）](https://technet.microsoft.com/library/ms179295.aspx)引用的当前客户端网络协议的名称。  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [配置客户端网络协议和网络库](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
