---
description: 比較運算子 (DMX)
title: " (DMX) 的比較運算子 |Microsoft Docs"
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0be897f827740a2a27ce3376df36ec0e296951b8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88395804"
---
# <a name="operators---comparison"></a>運算子 - 比較
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  在中，您可以使用比較運算子搭配任何資料採礦延伸模組中的純量資料 (DMX) 運算式 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。 比較運算子會評估為布林資料類型；它們會根據測試條件的結果而傳回 TRUE 或 FALSE。  
  
 下表會識別 DMX 支援的比較運算子。  
  
|運算子|描述|  
|--------------|-----------------|  
|[&#60; &#40;小於&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值小於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
|[&#62; &#40;大於&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值大於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
|[= &#40;等於&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值等於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
|[&#60;&#62; &#40;不等於&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值不等於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
|[&#60;= &#40;小於或等於&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值小於或等於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
|[&#62;= &#40;大於或等於&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值大於或等於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
  
 您也可以在 DMX 陳述式與函數中使用比較運算子尋找條件。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;DMX&#41; 參考的資料採礦延伸模組](../dmx/data-mining-extensions-dmx-reference.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 函數參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 語句參考](../dmx/data-mining-extensions-dmx-statements.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 語法慣例](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 語法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [DMX&#41;的運算式 &#40;](../dmx/expressions-dmx.md)   
 [&#40;DMX&#41;的一般預測函數 ](../dmx/general-prediction-functions-dmx.md)   
 [DMX &#40;的運算子&#41;](../dmx/operators-dmx.md)   
 [DMX 預測查詢的結構和使用方式](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 陳述式](../dmx/understanding-the-dmx-select-statement.md)  
  
  
