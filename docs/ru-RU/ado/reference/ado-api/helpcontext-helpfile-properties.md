---
title: HelpContext, HelpFile свойства | Документы Microsoft
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
- Error::GetHelpContext
- Error::GetHelpFile
- Error::get_HelpFile
- Error::get_HelpContext
- Error::HelpContext
- Error::HelpFile
helpviewer_keywords:
- HelpContext property [ADO]
- HelpFile property [ADO]
ms.assetid: 2b9ef441-993c-44d4-8f87-fac0979dac1d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74b6cab9fdd337bef8b36da027abbd7d7d87bb57
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="helpcontext-helpfile-properties"></a>HelpContext HelpFile свойства
Указывает файл справки и раздел, связанный с [ошибка](../../../ado/reference/ado-api/error-object.md) объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
  
-   **Идентификатор справки** возвращает идентификатор контекста, в виде **длинные** значение для раздела в файле справки.  
  
-   **HelpFile** возвращает **строка** значение, результатом которого является полностью разрешенной путь к файлу справки.  
  
## <a name="remarks"></a>Замечания  
 Если файл справки указан в **HelpFile** свойства **HelpContext** свойство используется для автоматического отображения раздела справки, он определяет. Если отсутствует соответствующий раздел справки отсутствует, **HelpContext** свойство возвращает ноль и **HelpFile** свойство возвращает строку нулевой длины (»»).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Описание, HelpContext, файл справки, NativeError, номер, источника и пример свойства SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Описание, HelpContext, файл справки, NativeError, номер, источник и пример свойства SQLState (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойство Description](../../../ado/reference/ado-api/description-property.md)   
 [Свойство номера (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Свойство Source (объект Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
