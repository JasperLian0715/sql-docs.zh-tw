---
description: SQL Server Native Client 錯誤 MSSQLSERVER_50000
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c0f5c601208aefcff17349a99318ce1160b7a108
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498835"
---
# <a name="sql-server-native-client-error-mssqlserver_50000"></a>SQL Server Native Client 錯誤 MSSQLSERVER_50000
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

    
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |
| --------- | ----- |
|產品名稱|SQL Server|  
|產品版本|11.0|  
|事件識別碼|50000|  
|事件來源|SETUP|  
|元件|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client|  
|符號名稱||  
|訊息文字|嘗試讀取檔案 '%.*ls' 時發生網路錯誤。|  
  
## <a name="explanation"></a>說明  
 嘗試在已經安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 而且現有安裝來自從 sqlncli.msi 重新命名之 MSI 檔案的電腦上安裝 (或更新) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請解除安裝現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 版本。 若要防止這個錯誤發生，請避免從不是名為 sqlncli.msi 的 MSI 檔案安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。  
  
## <a name="internal-only"></a>僅供內部使用  
  
