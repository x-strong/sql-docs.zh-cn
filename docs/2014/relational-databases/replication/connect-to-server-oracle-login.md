---
title: 连接到服务器 (Oracle)，登录名 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23f5b515fcb1e80416d860e2ff3a2e6be5431819
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010930"
---
# <a name="connect-to-server-oracle-login"></a>连接到服务器 (Oracle)，登录名
  使用“连接到服务器”对话框的“登录名”选项卡，指定   分发服务器与 Oracle 发布服务器建立连接时使用的帐户  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 所使用的帐户必须是配置发布服务器期间为复制管理用户架构指定的同一帐户。 有关详细信息，请参阅[配置 Oracle 发布服务器](non-sql/configure-an-oracle-publisher.md)。  
  
## <a name="options"></a>选项  
 **服务器实例**  
 Oracle 发布服务器的透明网络底层 (TNS)，是在配置分发服务器上安装的 Oracle 客户端软件期间指定的。  
  
 **身份验证**  
 选择 **“Oracle 标准身份验证”** （建议）或 **“Windows 身份验证”** 。 如果选择了 **“Windows 身份验证”** ，则：  
  
-   必须将 Oracle 服务器配置为允许使用 Windows 凭据进行连接。 有关详细信息，请参阅 Oracle 文档。  
  
-   当前的登录帐户必须与为复制管理用户架构指定的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户相同。  
  
 **“登录名”** 和 **“密码”**  
 如果在 **“身份验证”** 选项中选择了 **“Oracle 标准身份验证”** ，请指定要使用的登录名和密码，且必须与为复制管理用户架构指定的登录名和密码相同。  
  
## <a name="see-also"></a>另请参阅  
 [Oracle 发布的术语词汇表](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
