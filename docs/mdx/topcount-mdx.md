---
title: TopCount (многомерные Выражения) | Документы Microsoft
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
- TOPCOUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- TopCount function
ms.assetid: 15026a8f-35c5-4307-8856-348f5c44bfd5
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 66fa6fb9929b62c99fa829b1a55cdfc93139ee7c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="topcount-mdx"></a>TopCount (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Сортирует набор по убыванию и возвращает заданное число элементов с самыми высокими значениями.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Замечания  
 Если числовое выражение указано, **TopCount** функция сортирует в порядке убывания кортежи в наборе указанный заданного набора по значениям числового выражения, вычисленного над заданным набором. После сортировки набора, **TopCount** затем функция возвращает заданное количество кортежей с самыми высокими значениями.  
  
> [!IMPORTANT]  
>  Как [BottomCount](../mdx/bottomcount-mdx.md) функции **TopCount** функция всегда нарушает иерархию.  
  
 Если числовое выражение не указано, функция возвращает набор элементов в естественном порядке без какой-либо сортировки аналогично [Head (MDX)](../mdx/head-mdx.md) функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается 10 дат с самыми высокими значениями по мере Internet Sales Amount:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `TOPCOUNT([Date].[Date].[Date].MEMBERS, 10, [Measures].[Internet Sales Amount])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере из категории Bike возвращаются первые пять элементов набора, содержащего все сочетания элементов с уровнем City в иерархии Geography в измерении Geography и все финансовые годы из иерархии Fiscal измерения Date, отсортированные по мере Reseller Sales Amount (начиная с элементов этого набора с наибольшим объемом продаж).  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopCount  
   ({[Geography].[Geography].[City].Members   
      *[Date].[Fiscal].[Fiscal Year].Members}  
   , 5  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
