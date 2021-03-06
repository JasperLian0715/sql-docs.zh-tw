---
description: Dialect 屬性
title: 方言屬性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
author: rothja
ms.author: jroth
ms.openlocfilehash: be93ceb76aa0aadba5b28673c16704b0881186f9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973899"
---
# <a name="dialect-property"></a>Dialect 屬性
表示 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) 或 [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) 屬性的方言。 此方言會定義提供者用來剖析字串或資料流程的語法和一般規則。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 **方言**屬性包含代表命令文字或資料流程方言的有效 GUID。 這個屬性的預設值為 {C8B521FB-5CF3-11CE-ADE5-00AA0044773D}，表示提供者應該選擇如何解讀命令文字或串流。  
  
## <a name="remarks"></a>備註  
 當使用者讀取這個屬性的值時，ADO 不會查詢提供者。它會傳回目前儲存在 [命令](../../../ado/reference/ado-api/command-object-ado.md) 物件中之值的字串表示。  
  
 當使用者設定 **方言** 屬性時，如果所提供的值不是有效的 guid，則 ADO 會驗證 GUID 並引發錯誤。 請參閱提供者的檔，以判斷 **方言** 屬性所支援的 GUID 值。  
  
## <a name="applies-to"></a>套用至  
 [Command 物件 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [Execute 方法 (ADO 命令)](../../../ado/reference/ado-api/execute-method-ado-command.md)
