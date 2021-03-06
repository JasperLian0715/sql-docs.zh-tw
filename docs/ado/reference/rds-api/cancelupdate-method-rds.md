---
description: CancelUpdate 方法 (RDS)
title: " (RDS) 的 CancelUpdate 方法 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CancelUpdate method [RDS]
ms.assetid: 76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650
author: rothja
ms.author: jroth
ms.openlocfilehash: 8cb9bcb9e0bf18cc2b6ab8d654eaccdc92ff7563
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722619"
---
# <a name="cancelupdate-method-rds"></a>CancelUpdate 方法 (RDS)
取消對 [記錄集](../ado-api/recordset-object-ado.md) 物件的目前或新資料列所做的任何變更。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，Windows 作業系統中不再包含 RDS 伺服器元件 (如需詳細) 資訊，請參閱 Windows 8 和 [Windows server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416) 。 未來的 Windows 版本將移除 RDS 用戶端元件。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該遷移至 [WCF 資料服務](/dotnet/framework/wcf/)。  
  
## <a name="syntax"></a>語法  
  
```  
  
DataControl.CancelUpdate  
```  
  
#### <a name="parameters"></a>參數  
 *DataControl*  
 代表 RDS 的物件變數 [。DataControl](./datacontrol-object-rds.md) 物件。  
  
## <a name="remarks"></a>備註  
 OLE DB 的資料指標服務會保留原始值的複本和變更的快取。 當您呼叫 **CancelUpdate**時，會將變更的快取重設為空白，並使用原始資料重新整理任何繫結控制項。  
  
## <a name="applies-to"></a>套用至  
 [DataControl 物件 (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>另請參閱  
 [ (VBScript) 的 CancelUpdate 方法範例 ](./cancelupdate-method-example-vbscript.md)   
 [通訊錄命令按鈕](../../guide/remote-data-service/address-book-command-buttons.md)   
 [ (ADO) 的 Cancel 方法 ](../ado-api/cancel-method-ado.md)   
 [ (RDS) 的 Cancel 方法 ](./cancel-method-rds.md)   
 [ (ADO) 的 CancelBatch 方法 ](../ado-api/cancelbatch-method-ado.md)   
 [ (ADO) 的 CancelUpdate 方法 ](../ado-api/cancelupdate-method-ado.md)   
 [ (RDS) 的 Refresh 方法 ](./refresh-method-rds.md)   
 [SubmitChanges 方法 (RDS)](./submitchanges-method-rds.md)