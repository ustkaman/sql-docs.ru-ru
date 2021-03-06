---
title: StrToSet (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STRTOSET
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToSet function
ms.assetid: 1700a563-6527-450a-8d3b-975c65bb6e51
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 34008751a017e97d353cca7c90db1de5e6710d98
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="strtoset-mdx"></a>StrToSet (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор, заданный строкой в формате многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StrToSet(Set_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Specification*  
 Допустимое строковое выражение, обозначающее (напрямую или косвенно) набор.  
  
## <a name="remarks"></a>Замечания  
 **StrToSet** функция возвращает набор, заданный строковым выражением. **StrToSet** функция обычно используется с определяемых пользователем функций для передачи спецификации набора из внешней функции обратно в инструкцию многомерных Выражений или параметризованный запрос многомерных Выражений.  
  
-   При использовании флага CONSTRAINED спецификация набора должна содержать полные или неполные имена элементов или набор кортежей, содержащий полные или неполные имена элементов заключены в фигурные скобки {}. Этот флаг используется для уменьшения риска атак, использующих вставку инструкций SQL в указанную строку. Если строка, которое не имена напрямую разрешаться в полное или неполное элементов, возникает следующая ошибка: «ограничения, установленные флагом CONSTRAINED функции STRTOSET нарушены.»  
  
-   Если флаг CONSTRAINED не используется, заданную спецификацию набора можно разрешить в допустимое многомерное выражение, возвращающее набор.  
  
-   Дополнительные сведения о различиях между наборами и элементами см. в разделах «Использование выражений наборов» и «Использование выражений элементов».  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается набор элементов иерархии атрибута State-Province, с помощью **StrToSet** функции. Указанная спецификация набора является допустимым многомерным выражением набора.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается сообщение об ошибке, поскольку используется флаг CONSTRAINED. Несмотря на то что заданная спецификация набора является допустимым многомерным выражением набора, она должна содержать полные или неполные имена элементов, поскольку указан флаг CONSTRAINED.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается мера Reseller Sales Amount для стран Germany и Canada. Указанная спецификация набора содержит полные имена элементов, как этого требует флаг CONSTRAINED.  
  
```  
SELECT StrToSet ('{[Geography].[Geography].[Country].[Germany],[Geography].[Geography].[Country].[Canada]}', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
