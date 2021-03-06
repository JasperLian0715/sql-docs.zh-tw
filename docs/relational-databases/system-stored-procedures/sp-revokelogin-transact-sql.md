---
description: sp_revokelogin (Transact-SQL)
title: sp_revokelogin (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokelogin_TSQL
- sp_revokelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokelogin
ms.assetid: cb1ab102-1ae0-4811-9144-9a8121ef2d7e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f2ccd140079e9a585ee67ce1b7c2208b9926f963
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446760"
---
# <a name="sp_revokelogin-transact-sql"></a>sp_revokelogin (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]針對使用 CREATE login、 **sp_grantlogin**或**Sp_denylogin**所建立的 Windows 使用者或群組，移除的登入專案。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md) 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>引數  
`[ @loginame = ] 'login'` 這是 Windows 使用者或群組的名稱。 *login* 是 **sysname**，沒有預設值。 *登*入可以是任何現有的 Windows 使用者名稱或群組，其格式為*電腦名稱稱* \\ *使用者或網域* \\ *使用者*。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 **sp_revokelogin** 使用 *login* 參數指定的帳號停用連接。 但是在撤銷其個別存取權之後，透過 Windows 群組成員資格獲得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體存取權的 Windows 使用者仍然可以用群組方式進行連接。 同樣地，如果 *login* 參數指定 Windows 群組的名稱，則該群組的成員會被個別授與實例的存取權， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仍然可以連接。  
  
 例如，如果 Windows 使用者 **ADVWORKS\john** 是 windows 群組 **ADVWORKS\Admins**的成員，且 **sp_revokelogin** 撤銷下列各項的存取權 `ADVWORKS\john` ：  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 如果**ADVWORKS\Admins**已被授與實例的存取權，則使用者**ADVWORKS\john**仍然可以連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 同樣地，如果 Windows 群組 **ADVWORKS\Admins** 撤銷其存取權，但 **ADVWORKS\john** 被授與存取權，則 **ADVWORKS\john** 仍可連接。  
  
 使用 **sp_denylogin** 明確防止使用者連接到的實例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，不論其 Windows 群組成員資格為何。  
  
 **sp_revokelogin** 無法在使用者自訂交易內執行。  
  
## <a name="permissions"></a>權限  
 需要伺服器的 ALTER ANY LOGIN 權限。  
  
## <a name="examples"></a>範例  
 下列範例會移除 Windows 使用者的登入專案 `Corporate\MollyA` 。  
  
```  
EXEC sp_revokelogin 'Corporate\MollyA';  
```  
  
 Or  
  
```  
EXEC sp_revokelogin [Corporate\MollyA];  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的安全性預存程式 ](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40;Transact-sql&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [sp_denylogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
