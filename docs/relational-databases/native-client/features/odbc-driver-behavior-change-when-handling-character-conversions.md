---
description: ODBC 驅動程式在處理字元轉換上的行為變更
title: ODBC 變更處理 char 轉換
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 48c2230327a92a560291aacbf802ae775b99fe8f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498885"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a>ODBC 驅動程式在處理字元轉換上的行為變更
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]Native CLIENT ODBC 驅動程式 ( # A0) 變更 SQL_WCHAR * (NCHAR/Nvarchar/Nvarchar (max) # A6 和 SQL_CHAR \* (CHAR/VARCHAR/NARCHAR (max) # A10 轉換。 當使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client ODBC 驅動程式時，ODBC 函數如 SQLGetData、SQLBindCol、SQLBindParameter 等傳回的長度/指標參數將會是 (-4) SQL_NO_TOTAL。 舊版的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式以往傳回長度值，而這可能不正確。  
  
## <a name="sqlgetdata-behavior"></a>SQLGetData 行為  
 許多 Windows 函數都可讓您指定緩衝區大小為 0，且傳回的長度會是所傳回資料的大小。 以下的寫法對 Windows 程式設計人員而言應已司空見慣：  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 不過，在此案例中不應使用 **SQLGetData** 。 請勿使用這種寫法：  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 只能呼叫**SQLGetData**來取出實際資料的區塊。 不支援使用 **SQLGetData** 來取得資料的大小。  
  
 以下說明當您使用不正確的寫法時，驅動程式變更所造成的影響。 此應用程式會查詢 **Varchar** 資料行，並以 Unicode (SQL_UNICODE/SQL_WCHAR) 進行系結：  
  
 查詢：  `select convert(varchar(36), '123')`  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式版本|長度或指標結果|描述|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client 或更早版本|6|驅動程式誤認為只要長度 * 2 即可將 CHAR 轉換成 WCHAR。|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (11.0.2100.60 版) 或更新版本|-4 (SQL_NO_TOTAL)|驅動程式不再假設從 CHAR 轉換成 WCHAR 或 WCHAR 至 CHAR 是 (乘以) \* 2 或 (除以) /2 動作。<br /><br /> 呼叫 **SQLGetData** 不會再傳回預期轉換的長度。 驅動程式將偵測出這是 CHAR 與 WCHAR 之間的相互轉換，並且傳回 (-4) SQL_NO_TOTAL 而不至於會有 *2 或 /2 的錯誤行為。|  
  
 使用 **SQLGetData** 來取出資料區塊。 (虛擬程式碼如下所示)  
  
```  
while( (SQL_SUCCESS or SQL_SUCCESS_WITH_INFO) == SQLFetch(...) ) {  
   SQLNumCols(...iTotalCols...)  
   for(int iCol = 1; iCol < iTotalCols; iCol++) {  
      WCHAR* pBufOrig, pBuffer = new WCHAR[100];  
      SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get original chunk  
      while(NOT ALL DATA RETREIVED (SQL_NO_TOTAL, ...) ) {  
         pBuffer += 50;   // Advance buffer for data retrieved  
         // May need to realloc the buffer when you reach current size  
         SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get next chunk  
      }  
   }  
}  
```  
  
## <a name="sqlbindcol-behavior"></a>SQLBindCol 行為  
 查詢：  `select convert(varchar(36), '1234567890')`  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式版本|長度或指標結果|描述|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client 或更早版本|20|**SQLFetch** 報告資料的右邊有截斷的情況。<br /><br /> 長度將是所傳回資料的長度，而非任何儲存的內容 (假象誤認為 *2 CHAR 可轉換成 WCHAR)。<br /><br /> 儲存在緩衝區內的資料是 123\0。 緩衝區一定是以 NULL 結尾。|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (11.0.2100.60 版) 或更新版本|-4 (SQL_NO_TOTAL)|**SQLFetch** 報告資料的右邊有截斷的情況。<br /><br /> 由於資料的其餘部分並未轉換，指出的長度為 -4 (SQL_NO_TOTAL)。<br /><br /> 儲存在緩衝區內的資料是 123\0。 - 緩衝區一定是以 NULL 結尾。|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a>SQLBindParameter (OUTPUT 參數行為)  
 查詢：  `create procedure spTest @p1 varchar(max) OUTPUT`  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式版本|長度或指標結果|描述|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client 或更早版本|2468|**SQLFetch** 傳回沒有任何可用的資料。<br /><br /> **SQLMoreResults** 傳回沒有任何可用的資料。<br /><br /> 指出的長度是從伺服器傳回之資料的大小，而非緩衝區內所儲存資料的大小。<br /><br /> 原始緩衝區內包含 63 個位元組和 NULL 結束字元。 緩衝區一定是以 NULL 結尾。|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (11.0.2100.60 版) 或更新版本|-4 (SQL_NO_TOTAL)|**SQLFetch** 傳回沒有任何可用的資料。<br /><br /> **SQLMoreResults** 傳回沒有任何可用的資料。<br /><br /> 由於資料的其餘部分並未轉換，指出的長度為 (-4) SQL_NO_TOTAL。<br /><br /> 原始緩衝區內包含 63 個位元組和 NULL 結束字元。 緩衝區一定是以 NULL 結尾。|  
  
## <a name="performing-char-and-wchar-conversions"></a>執行 CHAR 和 WCHAR 轉換  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC 驅動程式提供了幾種方法來執行 CHAR 和 WCHAR 轉換。 邏輯類似于將 blob 操作 (Varchar (max) 、Nvarchar (max) 、... ) ：  
  
-   使用 **SQLBindCol** 或 **SQLBindParameter**系結時，資料會儲存或截斷至指定的緩衝區。  
  
-   如果您未系結，您可以使用 **SQLGetData** 和 **SQLParamData**，以區塊形式取出資料。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client 功能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
