---
title: Поля коллекции (ADO) | Документы Microsoft
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
- Fields
- Recordset15::Fields
- _Record::Fields
helpviewer_keywords:
- Fields collection [ADO]
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8dbbda5d1aa43b71820da792cb67c6ad68314adc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="fields-collection-ado"></a>Коллекция Fields (ADO)
Содержит все [поле](../../../ado/reference/ado-api/field-object.md) объектов [записей](../../../ado/reference/ado-api/recordset-object-ado.md) или [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта.  
  
## <a name="remarks"></a>Замечания  
 Объект **записей** объект имеет **поля** коллекцию, состоящую из **поле** объектов. Каждый **поле** объекта соответствует столбцу в **записей**. Можно заполнить **поля** коллекции перед открытием **записей** путем вызова [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод для коллекции.  
  
> [!NOTE]
>  . В разделе **поле** разделе объекта более подробное описание использования **поле** объектов.  
  
 **Поля** коллекция [Append](../../../ado/reference/ado-api/append-method-ado.md) метод, который предварительно создает и добавляет **поле** в коллекцию и **обновить**метод, который завершает добавлений или удалений.  
  
 Объект **запись** объект имеет два специальных поля могут быть проиндексированы с [FieldEnum](../../../ado/reference/ado-api/fieldenum.md) константы. Один константа обращается к полю, содержащему потока по умолчанию для **запись**, и другой обращается к полю, содержащему строке абсолютный URL-адреса для **записи**.  
  
 Некоторых поставщиков (например, [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) может заполнить **поля** коллекции с подмножеством доступных полей для **записи** или **записей**. Другие поля не добавляются в коллекцию до сначала по имени или проиндексирован кода.  
  
 При попытке ссылки на несуществующие поле по имени, новый **поле** объекта будет добавлена к **поля** коллекции с [состояние](../../../ado/reference/ado-api/status-property-ado-field.md) из  **adFieldPendingInsert**. При вызове [обновление](../../../ado/reference/ado-api/update-method.md), ADO будет создать новое поле в источнике данных, если это разрешено поставщиком.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства коллекции полей, методов и событий](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)
