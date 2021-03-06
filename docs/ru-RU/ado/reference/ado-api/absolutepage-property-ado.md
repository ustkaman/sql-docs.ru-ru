---
title: Свойство AbsolutePage (ADO) | Документы Microsoft
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
- Recordset15::AbsolutePage
helpviewer_keywords:
- AbsolutePage property [ADO]
ms.assetid: ddb58a35-ec3a-423c-a504-3c65e62c23d4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b87d45f01948cf5cdfa60ed1bf185a96be4c495c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="absolutepage-property-ado"></a>Свойство AbsolutePage (ADO)
Указывает, на какой странице находится текущая запись.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 32-разрядный код задает или возвращает **длинные** значение от 1 до числа страниц в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта ([PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)), или возвращает одно из [PositionEnum ](../../../ado/reference/ado-api/positionenum.md) значения.  
  
 Для 64-разрядного кода используйте тип данных, который обеспечивает хранение 64-разрядное значение. Например, можно использовать либо **длинные** или другое значение, которое может иметь длину 64-разрядной, например DBORDINAL. Не используйте **PositionEnum** значения, поскольку они ограничены длиной 32 бит.  
  
## <a name="remarks"></a>Замечания  
 Это свойство может использоваться для идентификации номер страницы, на котором расположена текущая запись. Она использует [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) свойство для логического разделения строк общее число **записей** объекта на последовательность страниц, каждая из которых имеет количество записей равно **PageSize** (за исключением последней страницы, которые могут иметь менее записей). Поставщик должен поддерживать соответствующие функциональные возможности для этого свойства доступно.  
  
-   При получении или установке **AbsolutePage** свойство, ADO использует [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) свойство и [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) свойство друг с другом, как показано ниже:  
  
-   Для получения **AbsolutePage**, сначала извлекает ADO **AbsolutePosition**и затем делит его **PageSize**.  
  
-   Чтобы задать **AbsolutePage**, перемещает ADO **AbsolutePosition** следующим образом: она умножает **PageSize** по новому **AbsolutePage** значение, а затем добавляет 1 к значению. В результате текущую позицию в **записей** после успешной установки **AbsolutePage** является первой записи на данной странице.  
  
 Как **AbsolutePosition** свойства **AbsolutePage** начинается с 1 и имеет значение 1, если текущая запись является первой записью в **записей**. Задайте это свойство, чтобы перейти к первой записи определенной страницы. Получить общее число страниц из **PageCount** свойство.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [AbsolutePage, PageCount и пример свойства PageSize (Visual Basic)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount и пример свойства PageSize (VC ++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Свойство AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [Свойство PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)   
 [Свойство PageSize (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)
