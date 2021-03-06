---
title: Intersect (многомерные Выражения) | Документы Microsoft
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
- INTERSECT
dev_langs:
- kbMDX
helpviewer_keywords:
- Intersect function
ms.assetid: 0de8fbb4-e2db-480c-86f1-2abbbcfdb1d8
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 9e308a9b4a01b7f70562c9c69b4d353a4e4d9198
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="intersect-mdx"></a>Intersect (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает пересечение двух входных наборов, при необходимости сохраняя повторяющиеся элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Intersect(Set_Expression1 , Set_Expression2 [ , ALL ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Замечания  
 **Intersect** функция возвращает пересечение двух множеств. По умолчанию эта функция удаляет дубликаты из обоих наборов до проведения операции над наборами. Оба набора должны иметь одинаковую размерность.  
  
 Необязательный **все** флаг сохраняет повторяющиеся значения. Если **все** указано, **Intersect** функция пересечение неповторяющихся элементов в обычном режиме и пересечение повторяющихся первого набора, который имеет повторяются во втором наборе. Оба набора должны иметь одинаковую размерность.  
  
## <a name="example"></a>Пример  
 Следующий запрос возвращает значения 2003 и 2004 годов. Эти два элемента присутствуют в обоих указанных наборах.  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001], [Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003]}`  
  
 `, {[Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 Следующий запрос завершается ошибкой, поскольку два заданных набора содержат элементы из различных иерархий.  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001]}`  
  
 `, {[Customer].[City].&[Abingdon]&[ENG]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
