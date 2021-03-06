---
description: ConnectionTimeout 屬性 (ADO)
title: " (ADO) 的 ConnectionTimeout 屬性 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
author: rothja
ms.author: jroth
ms.openlocfilehash: bd8fd11c017583ef49981021688210245589e971
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974739"
---
# <a name="connectiontimeout-property-ado"></a>ConnectionTimeout 屬性 (ADO)
指出在結束嘗試並產生錯誤之前，建立連接所需等待的時間。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回 **long** 值，指出等候連接開啟的時間（以秒為單位）。 預設值為 15。  
  
## <a name="remarks"></a>備註  
 如果從網路流量或使用繁重的伺服器來延遲，請在[連接](./connection-object-ado.md)物件上使用**ConnectionTimeout**屬性，讓它必須放棄連線嘗試。 如果 [ **ConnectionTimeout** ] 屬性設定的時間在開啟連接之前已過，則會發生錯誤，而 ADO 會取消嘗試。 如果您將屬性設定為零，則 ADO 會無限期等候，直到開啟連接為止。 請確定您撰寫程式碼的提供者支援 **ConnectionTimeout** 功能。  
  
 當連線關閉時， **ConnectionTimeout** 屬性是讀取/寫入，而當連接開啟時，則為唯讀屬性。  
  
## <a name="applies-to"></a>套用至  
 [Connection 物件 (ADO)](./connection-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [ConnectionString、ConnectionTimeout 和 State 屬性範例 (VB) ](./connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、ConnectionTimeout 和 State 屬性範例 (VC + +) ](./connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [CommandTimeout 屬性 (ADO)](./commandtimeout-property-ado.md)