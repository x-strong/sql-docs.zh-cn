---
title: 使用安全 Web 服务方法 | Microsoft Docs
description: 需要使用 RSReportServer 配置文件中的 SecureConnectionLevel 设置为报表服务器 Web 服务方法建立安全连接。
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c29c7d6d1a8fb8be7edff1203073c4c84d2e197c
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487406"
---
# <a name="using-secure-web-service-methods"></a>使用安全 Web 服务方法
  当您调用某些报表服务器 Web 服务方法时，它们可能要求安全连接。 要求安全连接的方法由 RSReportServer.config 文件中的 SecureConnectionLevel  设置确定。 该设置的值是整数值，大于等于 0 即可。 下表介绍了这些值。  
  
|级别|说明|  
|-----------|-----------------|  
|**0**|不安全。 对 Reporting Services SOAP API 的调用不要求安全连接。|  
|大于“0” |安全。 对 Reporting Services SOAP API 所进行的所有调用都要求安全连接。|  
  
 可以使用 Web 服务的 <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> 方法返回根据报表服务器的当前配置要求安全连接的 Web 服务方法列表。 在 TLS 方案中，应评估由 <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> 返回的方法列表，并将 Web 服务 URI 的架构名称更改为“https”或“http”（具体视所调用的方法而定）。  
  
## <a name="see-also"></a>另请参阅  
 [使用 Web 服务和 .NET Framework 生成应用程序](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [报表服务器 Web 服务](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
