---
description: 配置連接控制代碼
title: 配置連接控制碼 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, passwords
- ODBC applications, connections
- handles [SQL Server Native Client]
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- SQL Server Native Client ODBC driver, connection handles
- connection handles [SQL Server Native Client]
- modifying passwords
- SQLAllocHandle function
ms.assetid: 471d8a31-199c-4f92-bb10-004fc7733b35
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b7c477627f8f4d8a4e060dcd29ab4c7fa97629d7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420702"
---
# <a name="allocating-a-connection-handle"></a>配置連接控制代碼
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  在應用程式可以連接到資料來源或驅動程式之前，必須配置連接控制代碼。 這是藉由呼叫 **SQLAllocHandle** ，並將 *HandleType* 參數設定為 SQL_HANDLE_DBC，並將 *InputHandle* 指向已初始化的環境控制碼來完成。  
  
 連接的特性是藉由設定連接屬性來控制。 例如，因為交易發生在連接層級，所以交易隔離等級是連接屬性。 同樣地，登入逾時 (也就是要在嘗試連接時，在逾時之前等候的秒數) 也是連接屬性。  
  
 連接屬性是使用 [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)設定的，而且其目前的設定會以 [SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)抓取。 如果在嘗試連接之前呼叫 **SQLSetConnectAttr** ，ODBC 驅動程式管理員會將屬性儲存在其連接結構中，並在連接過程中將它們設定在驅動程式中。 有些連接屬性必須在應用程式嘗試連接之前設定，其他的屬性則可以在連接完成之後設定。 例如，SQL_ATTR_ODBC_CURSORS 必須在進行連接之前設定，但 SQL_ATTR_AUTOCOMMIT 可以在連接之後設定。  
  
 針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 版或更新版本執行的應用程式，有時可以藉由重設表格式資料流 (TDS) 網路封包大小來改善其效能。 預設封包大小是 4 KB，設定於伺服器。 4 KB 到 8 KB 的封包大小一般可提供最佳效能。 如果測試顯示應用程式使用其他封包大小時效能較佳，則可以重設封包大小。 ODBC 應用程式可以使用 SQL_ATTR_PACKET_SIZE 選項來呼叫 **SQLSetConnectAttr** ，以進行連接。 有些應用程式在使用較大封包大小時效能較佳，但一般而言，封包大小大於 8 KB 時所能改進的效能微乎其微。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式具有一些擴充連接屬性，可讓應用程式用來增加其功能。 這其中有些屬性所控制的選項，可在資料來源中指定並用來覆寫資料來源中所設的任何選項。 例如，如果應用程式使用引號識別碼，則可以將驅動程式特定的屬性 SQL_COPT_SS_QUOTED_IDENT 設為 SQL_QI_ON，以確保一定可以設定此選項，不論資料來源中的設定為何。  
  
## <a name="see-also"></a>另請參閱  
 [與 SQL Server &#40;ODBC&#41;通訊 ](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
