---
title: Свойство ParentCatalog (ADOX) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User::get_ParentCatalog
- _Column::ParentCatalog
- _Table::put_ParentCatalog
- _Group::put_ParentCatalog
- _Column::get_ParentCatalog
- _Table::PutParentCatalog
- _Group::putref_ParentCatalog
- _Group::ParentCatalog
- _Column::PutParentCatalog
- _Column::put_ParentCatalog
- _Group::get_ParentCatalog
- _User::put_ParentCatalog
- _User::putref_ParentCatalog
- _Table::get_ParentCatalog
- _Group::PutParentCatalog
- _Table::ParentCatalog
- _Column::GetParentCatalog
- _Table::PutRefParentCatalog
- _User::GetParentCatalog
- _Table::GetParentCatalog
- _Table::putref_ParentCatalog
- _User::PutParentCatalog
- _User::ParentCatalog
- _User::PutRefParentCatalog
- _Group::GetParentCatalog
- _Group::PutRefParentCatalog
helpviewer_keywords:
- ParentCatalog property [ADOX]
ms.assetid: a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45548fec3e60a12cf2c74218ed8ab5603fa26899
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="parentcatalog-property-adox"></a>Свойство ParentCatalog (ADOX)
Указывает каталог родительского объекта таблицы, пользователя или столбца для предоставления доступа к свойствам конкретного поставщика.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) объекта. Установка **ParentCatalog** открытому **каталога** разрешает доступ к свойствам определенного поставщика перед добавлением, таблицу или столбец для **каталога** коллекции.  
  
## <a name="remarks"></a>Замечания  
 Некоторые поставщики данных допускает значения свойства поставщика для записи только в момент создания: то есть, когда таблицы или столбца добавляется к его **каталога** коллекции. Для доступа к этим свойствам перед добавлением эти объекты, и **каталога**, укажите **каталога** в **ParentCatalog** свойства первого.  
  
 Ошибка возникает, когда таблица или столбец добавляется к другому **каталога** чем **ParentCatalog**.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|  
|[Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)||  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
