---
title: 其他批註（SQLXML）
description: 查看 SQLXML 批註的清單，其中包含 XML 大量載入如何解讀每一個的說明。
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6780a99b5bca826a9e92890ebe317f32c93300fc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85724734"
---
# <a name="annotation-interpretation---other-annotations"></a>註解解譯 - 其他註解
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  除了本章節先前的主題所討論的註解以外，XML 大量載入還會解譯這些其他註解，如下所示：  
  
 **sql:id-prefix**  
 如果結構描述指定 XML 資料的前置詞，XML 大量載入會先移除這些前置詞，然後再將資料傳送給 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。  
  
 **sql:use-cdata**  
 XML 大量載入會讀取 CDATA 區段中所儲存的文字，然後將其傳送給 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。  
  
 **sql:url-encode**  
 XML 大量載入不支援此註釋。 例如，您不能在 XML 資料輸入中指定 URL，然後預期 XML 大量載入會從該位置讀取資料，將它儲存在資料庫中。  
  
 **sql:is-mapping-schema**  
 XML 大量載入不支援此注釋，也不支援**sql： id**。  
  
> [!NOTE]  
>  XML 大量載入不支援內嵌對應結構描述。  
  
 **sql:key-fields**  
 XML 大量載入一定會忽略此註解。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;SQLXML 4.0&#41;的注釋轉譯](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sqlxml-4-0.md)  
  
  
