---
title: Свойство DateModified (ADOX) | Документы Microsoft
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
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords:
- DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8aec8a002bd7f3ac77ff051b100e4a7ffcf6876b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="datemodified-property-adox"></a>Свойство DateModified (ADOX)
Указывает дату последнего изменения объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **Variant** значение, указывающее, изменен. Имеет значение null при **DateModified** не поддерживается поставщиком.  
  
## <a name="remarks"></a>Замечания  
 **DateModified** свойство имеет значение null для добавленного объектов. После добавления нового [представление](../../../ado/reference/adox-api/view-object-adox.md) или [процедура](../../../ado/reference/adox-api/procedure-object-adox.md), необходимо вызвать [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод [представления](../../../ado/reference/adox-api/views-collection-adox.md) или [процедуры ](../../../ado/reference/adox-api/procedures-collection-adox.md) коллекции для получения значений для **DateModified** свойство.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Объект View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>См. также  
 [DateCreated и DateModified-пример свойства (Visual Basic)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Свойство DateCreated (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
