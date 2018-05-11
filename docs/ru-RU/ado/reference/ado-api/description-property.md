---
title: Свойство Description | Документы Microsoft
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
- Error::Description
- Error::GetDescription
- Error::get_Description
helpviewer_keywords:
- Description property
ms.assetid: 4b5d6790-6c29-42aa-bf78-d9cfb8ad7965
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbf735e766e6ff4e058aee7c8c7f1ee9682b0339
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="description-property"></a>Свойство Description
Описывает [ошибка](../../../ado/reference/ado-api/error-object.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строка** значение, содержащее описание ошибки.  
  
## <a name="remarks"></a>Замечания  
 Используйте **описание** , чтобы получить краткое описание ошибки. Отображать это свойство, чтобы предупредить пользователя об ошибке, не может или не требуется обработать. Строка будет получен из ADO или поставщика.  
  
 Поставщики отвечают передачи конкретного текста ошибки для ADO. Добавляет ADO [ошибка](../../../ado/reference/ado-api/error-object.md) объект **ошибки** коллекции для каждого поставщика ошибка или предупреждение, он получает. Перечисление **ошибки** коллекции для трассировки ошибок, которые этот поставщик передает.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Описание, HelpContext, файл справки, NativeError, номер, источника и пример свойства SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Описание, HelpContext, файл справки, NativeError, номер, источник и пример свойства SQLState (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [HelpContext HelpFile свойства](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Свойство номера (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Свойство Source (объект Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)