---
title: XOR (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft
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
- XOR
dev_langs:
- kbMDX
helpviewer_keywords:
- XOR operator
ms.assetid: 17280f36-df0e-477e-9342-e8129ed5cc3c
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 17bebf33ae3cc5d08f51fe61ac7adbe0de875751
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="xor-mdx"></a>XOR (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет логическое исключение над двумя числовыми выражениями.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
 *Expression2*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, которое возвращает **true** Если один и только один аргумент принимает значение **true**; в противном случае **false**.  
  
## <a name="remarks"></a>Замечания  
 **XOR** оператор рассматривает оба аргумента как логические значения (ноль, 0 — как **false**; в противном случае **true**), прежде чем оператор выполнит логическое исключение. В следующей таблице показано, как **XOR** оператор выполняет логическое исключение.  
  
|*Expression1*|*Expression2*|Возвращаемое значение|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**false**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
