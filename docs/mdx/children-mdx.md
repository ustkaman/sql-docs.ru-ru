---
title: Children (многомерные Выражения) | Документы Microsoft
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
- CHILDREN
dev_langs:
- kbMDX
helpviewer_keywords:
- Children function
ms.assetid: ce2c3069-914c-44a3-8a4c-5cbd4fb71e4c
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c557f98ad428f885066cb1df88c1edc177587479
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="children-mdx"></a>Children (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор потомков указанного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 **Дочерних** функция возвращает естественно упорядоченный набор, содержащий потомки заданного элемента. Если у элемента нет потомков, функция возвращает пустой набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращаются потомки элемента United States в иерархии Geography измерения Geography.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 Следующий пример возвращает все элементы в **меры** измерение по оси столбцов, это включает в себя все вычисляемые элементы и набор всех потомков `[Product].[Model Name]` иерархии на оси строк из атрибута **Adventure Works** куба.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|Выпуск|Журнал|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**Измененное содержимое:**<br /> — Обновлены синтаксис и аргументы для облегчения понимания.<br /><br /> — Добавлены обновленные примеры.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
