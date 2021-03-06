---
title: Инструкции CALL (многомерные Выражения) | Документы Microsoft
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
- CALL
dev_langs:
- kbMDX
helpviewer_keywords:
- voids [MDX]
- stored procedures [MDX]
- CALL statement
ms.assetid: b534a20b-924c-43b8-832d-24e57d50425c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 079f29676bd1f71d70e182af2ee8664361916d49
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-manipulation---call"></a>Управление данными MDX - ВЫЗОВ
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет хранимую процедуру, которая возвращает значение void в текущей области или (по желанию) в указанном кубе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CALL SP_Name   
   [ (SP_Argument   
      [, SP_Argument ,...n]  
      ) ]   
[ONCube_Expression]  
```  
  
## <a name="arguments"></a>Аргументы  
 *SP_Name*  
 Допустимое строковое выражение, представляющее имя хранимой процедуры.  
  
 *SP_Argument*  
 Допустимое строковое выражение, представляющее аргумент хранимой процедуры.  
  
 *Cube_Expression*  
 Допустимое строковое выражение куба, представляющее имя куба.  
  
## <a name="remarks"></a>Замечания  
 **ВЫЗОВИТЕ** инструкция запускает указанный регистрируемой хранимой процедуры, включая при необходимости один или несколько аргументов для указанной хранимой процедуры. **ВЫЗОВИТЕ** инструкция предназначена для использования только с помощью хранимых процедур, возвращающих значение void. Ее нельзя сочетать с другими функциями и операторами в многомерном выражении. Зарегистрированные хранимые процедуры, возвращающие значения, можно явно вызывать в многомерных выражениях и использовать совместно с другими функциями и операторами многомерных выражений.  
  
 Если куб не указан, инструкция выполняет хранимую процедуру над текущим кубом.  
  
> [!NOTE]  
>  Если хранимая процедура не зарегистрирована на компьютере клиента, **вызвать** оператор пытается вызвать хранимую процедуру из экземпляра [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Инструкции языка манипулирования данными &#40;многомерных Выражений&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Использование хранимых процедур (MDX)](../mdx/using-stored-procedures-mdx.md)  
  
  
