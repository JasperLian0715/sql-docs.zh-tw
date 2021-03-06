---
description: sp_helpdb (Transact-SQL)
title: sp_helpdb (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdb
- sp_helpdb_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdb
ms.assetid: 4c3e3302-6cf1-4b2b-8682-004049b578c3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b1b2055f810be69949f72dd97364ccfb47bfa22f
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809158"
---
# <a name="sp_helpdb-transact-sql"></a>sp_helpdb (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  報告指定的資料庫或所有資料庫的相關資訊。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpdb [ [ @dbname= ] 'name' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @dbname = ] 'name'` 這是要報告其資訊的資料庫名稱。 *名稱* 是 **sysname**，沒有預設值。 如果未指定*name* ，則會在**sys.databases**目錄檢視中的所有資料庫上**sp_helpdb**報表。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|資料庫名稱。|  
|**db_size**|**Nvarchar (13) **|資料庫的總大小。|  
|**擁有者**|**sysname**|資料庫擁有者，例如 **sa**。|  
|**dbid**|**smallint**|資料庫識別碼。|  
|**created**|**nvarchar(11)**|資料庫的建立日期。|  
|**status**|**Nvarchar (600) **|資料庫目前所設定的資料庫選項值清單 (以逗號分隔)。<br /><br /> 布林值選項必須已啟用，才會列出。 非布林值的選項會以*option_name*值的形式，以其對應的值列出 = * *。<br /><br /> 如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)。|  
|**compatibility_level**|**tinyint**|資料庫相容性層級：60、65、70、80 或 90。|  
  
 如果指定了 *name* ，則會有一個額外的結果集，顯示指定資料庫的檔案配置。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**nchar(128)**|邏輯檔案名稱。|  
|**fileid**|**smallint**|檔案識別碼。|  
|**filename**|**Nchar (260) **|作業系統檔案名稱 (實體檔案名稱)。|  
|**filegroup**|**nvarchar(128)**|檔案所屬的檔案群組。<br /><br /> NULL = 檔案是記錄檔。 它永遠不在檔案群組中。|  
|**size**|**Nvarchar (18) **|檔案大小 (以 MB 為單位)。|  
|**maxsize**|**Nvarchar (18) **|檔案所能成長的大小上限。 這個欄位中的 UNLIMITED 值指出，檔案將成長到磁碟已滿。|  
|**增長**|**Nvarchar (18) **|檔案的成長遞增。 這表示每次需要新空間時，檔案所增加的空間量。|  
|**使用**|**Varchar (9) **|檔案的使用方式。 針對資料檔案，值為「 **僅限資料** 」，而針對記錄檔，其值為「 **僅限記錄**」。|  
  
## <a name="remarks"></a>備註  
 結果集中的 [ **狀態** ] 資料行會報告資料庫中已設定為 [開啟] 的選項。 [ **狀態** ] 資料行不會報告所有資料庫選項。 若要查看目前資料庫選項設定的完整清單，請使用 **sys. 資料庫** 目錄檢視。  
  
## <a name="permissions"></a>權限  
 指定單一資料庫時，需要資料庫中 **public** 角色的成員資格。 如果未指定任何資料庫，則需要**master**資料庫中**public**角色的成員資格。  
  
 如果無法存取資料庫， **sp_helpdb** 會顯示錯誤訊息15622，以及資料庫的最多相關資訊。  
  
## <a name="examples"></a>範例  
  
### <a name="a-returning-information-about-a-single-database"></a>A. 傳回單一資料庫的相關資訊  
 下列範例會顯示 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的相關資訊。  
  
```sql  
EXEC sp_helpdb N'AdventureWorks2012';  
```  
  
### <a name="b-returning-information-about-all-databases"></a>B. 傳回所有資料庫的相關資訊  
 下列範例會顯示執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的伺服器之所有資料庫的相關資訊。  
  
```sql  
EXEC sp_helpdb;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的資料庫引擎預存程式 ](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
