---
title: Группы объектов (ADOX) | Документы Microsoft
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
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d08fc69680dbd4126073435b6267dd0cb0dd5ca7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="group-object-adox"></a>Объект группы (ADOX)
Представляет учетную запись группы, имеющую разрешения на доступ в защищенной базы данных.  
  
## <a name="remarks"></a>Замечания  
 [Группы](../../../ado/reference/adox-api/groups-collection-adox.md) коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет учетные записи групп каталога. **Группы** коллекции для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) представляет группу, к которой принадлежит пользователь.  
  
 С помощью свойств, коллекций и методов **группы** объекта, вы можете:  
  
-   Идентифицировать группу с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойства.  
  
-   Проверить группу чтения, записи или удаления разрешений с [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) и [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) методы.  
  
-   Доступ к учетные записи пользователей, имеющих членства в группе с [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) коллекции.  
  
-   Доступ к свойствам определенного поставщика с [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Group](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Коллекция групп (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
