---
description: sys.dm_os_memory_cache_hash_tables (Transact-SQL)
title: sys. dm_os_memory_cache_hash_tables (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_hash_tables_TSQL
- sys.dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_hash_tables dynamic management view
ms.assetid: 68b94f35-8f80-4d2b-bcde-7a21934219af
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0013d45519560f6bda0437f2977a1d071dd1b424
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546533"
---
# <a name="sysdm_os_memory_cache_hash_tables-transact-sql"></a>sys.dm_os_memory_cache_hash_tables (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中的每一個作用中快取，各傳回一個資料列。  
  
> [!NOTE]  
>  若要從或呼叫這個 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ，請使用名稱 **sys. dm_pdw_nodes_os_memory_cache_hash_tables**。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|快取項目的位址 (主索引鍵)。 不可為 Null。|  
|**name**|**nvarchar(256)**|快取的名稱。 不可為 Null。|  
|**type**|**nvarchar(60)**|快取的類型。 不可為 Null。|  
|**table_level**|**int**|雜湊資料表號碼。 一個特定快取可以有多個雜湊資料表對應到不同的雜湊函數。 不可為 Null。|  
|**buckets_count**|**int**|雜湊資料表中的值區數。 不可為 Null。|  
|**buckets_in_use_count**|**int**|目前使用的值區數。 不可為 Null。|  
|**buckets_min_length**|**int**|值區的最小快取項目數。 不可為 Null。|  
|**buckets_max_length**|**int**|值區的最大快取項目數。 不可為 Null。|  
|**buckets_avg_length**|**int**|每一個值區的平均快取項目數。 不可為 Null。|  
|**buckets_max_length_ever**|**int**|自從伺服器啟動之後，這份雜湊資料表之雜湊值區的最大快取項目數。 不可為 Null。|  
|**hits_count**|**bigint**|快取叫用數。 不可為 Null。|  
|**misses_count**|**bigint**|快速遺漏數。 不可為 Null。|  
|**buckets_avg_scan_hit_length**|**int**|在找到搜尋的項目之前，值區的平均檢查項目數。 不可為 Null。|  
|**buckets_avg_scan_miss_length**|**int**|在搜尋未成功結束之前，值區的平均檢查項目數。 不可為 Null。|  
|**pdw_node_id**|**int**|此散發所在之節點的識別碼。<br /><br /> **適用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>權限 

在上 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ，需要 `VIEW SERVER STATE` 許可權。   
在進階層中 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] ，需要 `VIEW DATABASE STATE` 資料庫中的許可權。 在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 標準和基本層中，需要  **伺服器管理員** 或 **Azure Active Directory 系統管理員** 帳戶。   

## <a name="see-also"></a>另請參閱  
 
  [SQL Server 作業系統相關的動態管理檢視 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


