---
title: 支持分布式事务 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
ms.assetid: d250b43b-9260-4ea4-90cc-57d9a2f67ea7
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 19378c7ead1ca34a6e3c2b42cb0b725560fabd8f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85658202"
---
# <a name="supporting-distributed-transactions"></a>支持分布式事务
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 访问接口使用者可以使用**ITransactionJoin：： JoinTransaction**方法参与由 Microsoft 分布式事务处理协调器（MS DTC）协调的分布式事务。  
  
 MS DTC 公开 COM 对象，这些对象允许客户端跨各种数据存储的多个连接来启动和参与协调的事务。 若要启动某个事务， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序使用者使用了 MS DTC **ITransactionDispenser**接口。 ITransactionDispenser 的 BeginTransaction 成员返回分布式事务对象的引用********。 使用 JoinTransaction 将此引用传递给 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供**JoinTransaction**程序。  
  
 MS DTC 支持对分布式事务的异步提交和中止。 为了通知异步事务状态，使用者实现 ITransactionOutcomeEvents 接口并将该接口与 MS DTC 事务对象连接****。  
  
 对于分布式事务， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序实现**ITransactionJoin：： JoinTransaction**参数，如下所示。  
  
|参数|描述|  
|---------------|-----------------|  
|punkTransactionCoord**|指向 MS DTC 事务对象的指针。|  
|IsoLevel**|由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序忽略。 使用者在从 MS DTC 获取事务对象时，确定由 MS DTC 协调的事务的隔离级别。|  
|IsoFlags**|必须为 0。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果使用者指定了其他任何值，则 Native Client OLE DB 提供程序将返回 XACT_E_NOISORETAIN。|  
|POtherOptions**|如果不为 NULL，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序从接口请求 options 对象。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果 options 对象的*ulTimeout*成员不为零，则 Native Client OLE DB 提供程序将返回 XACT_E_NOTIMEOUT。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序忽略*szDescription*成员的值。|  
  
 下面的示例通过使用 MS DTC 来协调事务：  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>另请参阅  
 [事务](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
