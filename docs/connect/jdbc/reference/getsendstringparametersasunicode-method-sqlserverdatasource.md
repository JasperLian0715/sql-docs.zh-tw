---
description: getSendStringParametersAsUnicode 方法 (SQLServerDataSource)
title: getSendStringParametersAsUnicode 方法 (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0fc9c5e4ba97f1e48e446768d59d5308604d5b29
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434580"
---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>getSendStringParametersAsUnicode 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回 **boolean** 值，此值會指出是否啟用以 UNICODE 格式將字串參數傳送至伺服器。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>傳回值  
 如果以 UNICODE 格式將字串參數傳送至伺服器，則為 **true**； 否則為 **false**。  
  
## <a name="remarks"></a>備註  
 如果 sendStringParametersAsUnicode 屬性設定為預設的 **true** 值，則字串參數就會以 UNICODE 格式傳送至伺服器。 如果 sendStringParametersAsUnicode 設定為 **false**，則字串參數就會以 ASCII/MBCS 格式而非 UNICODE 格式傳送至伺服器。 如果 sendStringParametersAsUnicode 未設定，getSendStringParametersAsUnicode 就會傳回預設值 **true**。  
  
 如需 sendStringParametersAsUnicode 連線屬性的詳細資訊，請參閱[設定連線屬性](../../../connect/jdbc/setting-the-connection-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
