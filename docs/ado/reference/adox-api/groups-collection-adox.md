---
title: "Группирует коллекцию (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3dfb8a9e2f75fb11caf64b06e34016474d7b9fa7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="groups-collection-adox"></a>Коллекция групп (ADOX)
Содержит все хранящиеся [группы](../../../ado/reference/adox-api/group-object-adox.md) объекты каталога или пользователя.  
  
## <a name="remarks"></a>Замечания  
 **Группы** коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет все учетные записи групп в каталоге. **Группы** коллекции для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) представляет группу, к которой принадлежит пользователь.  
  
 [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) метод **группы** является уникальным для ADOX. Возможные действия:  
  
-   Добавить новую группу безопасности в коллекцию с **Append** метод.  
  
 Остальные свойства и методы являются стандартными коллекциям ADO. Возможные действия:  
  
-   Доступ к группе в коллекции с [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Возвращает количество групп, содержащихся в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Удаление группы из коллекции с [удалить](../../../ado/reference/adox-api/delete-method-adox-collections.md) метод.  
  
-   Обновление объектов в коллекции в соответствии с текущей схемы базы данных с [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
> [!NOTE]
>  Перед добавлением **группы** объект **группы** коллекцию **пользователя** объекта, **группы** с тем же [ Имя](../../../ado/reference/adox-api/name-property-adox.md) как один, который будет добавляться уже должен существовать в **группы** коллекцию **каталога**.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства коллекции групп, методы и события](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект группы (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)