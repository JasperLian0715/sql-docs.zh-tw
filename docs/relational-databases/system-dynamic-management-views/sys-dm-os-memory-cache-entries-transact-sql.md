---
description: sys.dm_os_memory_cache_entries (Transact-SQL)
title: sys. dm_os_memory_cache_entries (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_memory_cache_entries
- sys.dm_os_memory_cache_entries
- dm_os_memory_cache_entries_TSQL
- sys.dm_os_memory_cache_entries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_entries dynamic management view
ms.assetid: dd32be6b-10d1-4059-b4fd-0bf817f40d54
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b29f7d03fc23fdb0d204de5f2f3cbd15bd6f74a7
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542140"
---
# <a name="sysdm_os_memory_cache_entries-transact-sql"></a>sys.dm_os_memory_cache_entries (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中傳回有關快取中所有項目的資訊。 使用這份檢視來追蹤其相關聯物件的快取項目。 您也可以使用這份檢視來取得快取項目的統計資料。  
  
> [!NOTE]  
>  若要從或呼叫這個 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ，請使用名稱 **sys. dm_pdw_nodes_os_memory_cache_entries**。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|快取的位址。 不可為 Null。|  
|**name**|**nvarchar(256)**|快取的名稱。 不可為 Null。|  
|**type**|**varchar(60)**|快取的類型。 不可為 Null。|  
|**entry_address**|**varbinary(8)**|快取項目的描述項位址。 不可為 Null。|  
|**entry_data_address**|**varbinary(8)**|快取項目的使用者資料位址。<br /><br /> 0x00000000 = 項目資料位址無法使用。<br /><br /> 不可為 Null。|  
|**in_use_count**|**int**|這個快取項目的並行使用者數目。 不可為 Null。|  
|**is_dirty**|**bit**|指出此快取項目是否已標記為要移除。 1 = 標示為移除。 不可為 Null。|  
|**disk_ios_count**|**int**|建立這個項目時產生的 I/O 數。 不可為 Null。|  
|**context_switches_count**|**int**|建立這個項目時產生的內容切換數目。 不可為 Null。|  
|**original_cost**|**int**|項目的原始成本。 這個值是產生的 I/O 數、CPU 指示成本和各項目耗用記憶體數量的近似值。 成本愈大，從快取中移除項目的機會愈小。 不可為 Null。|  
|**current_cost**|**int**|快取項目的目前成本。 在項目清除處理期間，會更新這個值。 當項目重複使用時，目前成本會重設為其原始值。 不可為 Null。|  
|**memory_object_address**|**varbinary(8)**|相關聯記憶體物件的位址。 可為 Null。|  
|**pages_allocated_count**|**bigint**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]。<br /><br /> 用來儲存這個快取項目的 8KB 頁數。 不可為 Null。|  
|**pages_kb**|**bigint**|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更新版本。<br /><br /> 此快取項目所使用的記憶體數量 (以 KB 為單位)。  不可為 Null。|  
|**entry_data**|**nvarchar(2048)**|快取項目的序列化表示法。 這項資訊視快取存放區而定。 可為 Null。|  
|**pool_id**|**int**|**適用對象**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更新版本。<br /><br /> 與項目相關聯的資源集區識別碼。 可為 Null。<br /><br /> 不是 katmai|  
|**pdw_node_id**|**int**|**適用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此散發所在之節點的識別碼。|  
  
## <a name="permissions"></a>權限 

在上 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ，需要 `VIEW SERVER STATE` 許可權。   
在進階層中 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] ，需要 `VIEW DATABASE STATE` 資料庫中的許可權。 在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 標準和基本層中，需要  **伺服器管理員** 或 **Azure Active Directory 系統管理員** 帳戶。   

## <a name="see-also"></a>另請參閱  
 
  [SQL Server 作業系統相關的動態管理檢視 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


