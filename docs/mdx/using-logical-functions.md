---
title: Использование логических функций | Документы Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- logical functions [MDX]
ms.assetid: 0cb34d53-9146-4924-9c9b-607afcb7a2be
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 3a206a7e83a8a2209cd6d521f17cdf8ee569a1d1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-logical-functions"></a>Использование логических функций
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Логическая функция выполняет логическую операцию или сравнение объектов и выражений, результатом вычисления логической функции будет логическое значение. В многомерных выражениях логические функции крайне важны для определения положения элементов.  
  
 Наиболее часто используемые Логическая функция — **IsEmpty** функции. Дополнительные сведения об использовании **IsEmpty** см. в разделе [пустые значения](../mdx/working-with-empty-values.md).  
  
 Следующий запрос показывает использование **IsLeaf** и **IsAncestor** функции:  
  
 `WITH`  
  
 `//Returns true if the CurrentMember on Calendar is a leaf member, ie it has no children`  
  
 `MEMBER MEASURES.[IsLeafDemo] AS IsLeaf([Date].[Calendar].CurrentMember)`  
  
 `//Returns true if the CurrentMember on Calendar is an Ancestor of July 1st 2001`  
  
 `MEMBER MEASURES.[IsAncestorDemo] AS IsAncestor([Date].[Calendar].CurrentMember, [Date].[Calendar].[Date].&[1])`  
  
 `SELECT{MEASURES.[IsLeafDemo],MEASURES.[IsAncestorDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;синтаксис многомерных Выражений&#41;](../mdx/functions-mdx-syntax.md)  
  
  
