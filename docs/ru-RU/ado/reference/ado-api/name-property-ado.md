---
title: Имя свойства (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Name
- Field20::Name
helpviewer_keywords:
- Name property [ADO]
ms.assetid: cfd0e29c-8310-44ab-85c3-5761184b865d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6fd84a300560dc124d52362be4a5a600824b1a0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="name-property-ado"></a>Свойство Name (ADO)
Указывает имя объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, указывающее имя объекта.  
  
## <a name="remarks"></a>Замечания  
 Используйте **имя** назначить имя, или получить имя свойства **команда**, **свойство**, **поле**, или **параметра**  объекта.  
  
 Значение — чтение и запись на **команда** объекта и только для чтения на **свойство** объекта.  
  
 Для **поле** объекта, **имя** обычно доступны только для чтения. Однако для новых **поле** объектов, добавленных в [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md), **имя** чтение и запись только в конце [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство **поле** был указан и поставщик данных успешно добавлен новый **поле** путем вызова [ Обновление](../../../ado/reference/ado-api/update-method.md) метод **поля** коллекции.  
  
 Для **параметр** объектов еще не добавлены [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции, **имя** свойство доступно для чтения/записи. Для добавлены **параметр** объекты и все другие объекты **имя** свойство доступно только для чтения. Имена не обязательно должны быть уникальными в пределах коллекции.  
  
 Вы можете получить **имя** свойство объекта по порядковому номеру, после чего можно ссылаться на объект напрямую по имени. Например если `rstMain.Properties(20).Name` дает `Updatability`, впоследствии можно ссылаться на это свойство как `rstMain.Properties("Updatability")`.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Field](../../../ado/reference/ado-api/field-object.md)|  
|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и примере имя свойства (Visual Basic)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Атрибуты и свойства пример имени (VC ++)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
