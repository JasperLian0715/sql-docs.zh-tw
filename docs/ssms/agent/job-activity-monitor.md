---
description: 作業活動監視器
title: 作業活動監視器
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.jobactivitymonitor.alljobs.f1
- SQL13.SWB.ACTIVITYMON.F1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 813740790db9a7f9bb15f8e5d2a003b73ba5a88f
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037941"
---
# <a name="job-activity-monitor"></a>作業活動監視器
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> [Azure SQL 受控執行個體](/azure/sql-database/sql-database-managed-instance)目前支援多數 (但非全部) 的 SQL Server Agent 功能。 如需詳細資料，請參閱 [Azure SQL 受控執行個體與 SQL Server 之間的 T-SQL 差異](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

使用此頁面即可檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業的目前活動。 按一下 [篩選]**** 即可限制顯示的作業。 [代理程式作業活動]**** 方格是唯讀的。 按一下資料行標頭即可排序方格。 若要修改作業，請按兩下作業以開啟 [作業屬性]**** 對話方塊。 以滑鼠右鍵按一下方格中的作業，即可開始執行所有作業步驟、於特定作業步驟開始、停用或啟用作業、重新整理作業、刪除作業、檢視作業的記錄或檢視作業的屬性。 按一下 [重新整理]****，以最新資訊更新方格。  
  
## <a name="options"></a>選項。  
**名稱**  
作業的名稱。  
  
**Enabled**  
不論作業為已啟用 ([是]****) 或未啟用 ([否]****)。  
  
**狀態***  
作業的目前狀態。  
  
**上次執行結果**  
作業上次執行的狀態。  
  
**最後執行**  
上次使用伺服器的當地日期和時間執行作業的日期和時間。  
  
**下次執行***  
下次排程為使用伺服器的當地日期和時間執行作業的日期和時間。  
  
**類別**  
指派給作業的作業類別目錄。  
  
**可執行的**  
[是]**** 如果作業可執行；[否]**** 如果作業無法執行。 如果作業沒有任何步驟，或者沒有目標伺服器，就無法執行此作業。  
  
**排程**  
[是]**** 表示作業已指派給作業排程；[否]**** 表示作業沒有排程。  
  
*只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員 (sysadmin) 固定伺服器角色和伺服器管理員群組的成員可以看到此資料行中的值。 SQLAgentOperatorRole 角色的成員無法看到此資料行中的值。  
  
#### <a name="to-open-the-job-activity-monitor"></a>若要開啟作業活動監視器  
  
-   在物件總管**** 中，依序展開伺服器和 [SQL Server Agent]****、以滑鼠右鍵按一下 [作業活動監視器]****，然後按一下 [檢視作業活動]****。  
  
## <a name="see-also"></a>另請參閱  
[監視作業活動](../../ssms/agent/monitor-job-activity.md)  
