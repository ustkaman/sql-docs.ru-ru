---
title: (Параметр ADO) свойство Size | Документы Microsoft
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
- _Parameter::Size
helpviewer_keywords:
- Size property [ADO Parameter]
ms.assetid: e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47cedd74ee305237f8c8a0eb0b0dd5903637a3a3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="size-property-ado-parameter"></a>Свойство Size (параметр ADO)
Указывает максимальный размер в байтах или символов, [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, указывающее максимальный размер в байтах или символов значения в **параметр** объекта.  
  
## <a name="remarks"></a>Замечания  
 Используйте **размер** определить максимальный размер значений записи или чтения из свойства [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство **параметр** объекта.  
  
 При указании типа данных переменной длины для **параметр** объекта (например, любой **строка** тип, например **adVarChar**), необходимо задать объекта  **Размер** свойство перед его добавлением [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции; в противном случае возникает ошибка.  
  
 Если уже добавленные **параметр** объект **параметры** коллекцию [команда](../../../ado/reference/ado-api/command-object-ado.md) объект и изменить его тип в тип данных переменной длины, необходимо задать **параметр** объекта **размер** свойство перед выполнением **команда** объекта; в противном случае возникает ошибка.  
  
 При использовании [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод, чтобы получить сведения о параметрах от поставщика и он возвращает тип данных переменной длины, один или несколько **параметр** объекты ADO может выделить память для параметров на основе на их максимальный потенциальный размер, который может вызвать ошибку во время выполнения. Чтобы предотвратить ошибку, необходимо явно задать **размер** свойства для этих параметров перед выполнением команды.  
  
 **Размер** свойство доступно для чтения/записи.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>См. также  
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление примере свойства (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Свойство Size (объект Stream ADO)](../../../ado/reference/ado-api/size-property-ado-stream.md)
