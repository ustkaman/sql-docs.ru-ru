---
title: Поддержка поставщика ADOX (ADO) | Документы Microsoft
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
helpviewer_keywords:
- ADOX provider support [ADO]
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 61cdd630dfefd4200007a3d3d1aad14aa68d9419
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="provider-support-for-adox-ado"></a>Поддержка поставщика ADOX (ADO)
Некоторые возможности ADOX не поддерживаются, в зависимости от поставщика данных OLE DB. ADOX полностью поддерживается с [поставщик OLE DB для Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md). Неподдерживаемые функции с [поставщик Microsoft OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), [поставщик Microsoft OLE DB для ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md), или [поставщик Microsoft OLE DB для Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) , перечисленные в следующих таблицах. Все прочие поставщики OLE DB для Microsoft ADOX не поддерживается.  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Поставщик Microsoft OLE DB для SQL Server  
  
|Объект или коллекция|Ограничение использования|  
|--------------------------|-----------------------|  
|**Таблицы** коллекции|Свойства доступны для чтения/записи до создания объекта и только для чтения при ссылке на существующий объект.|  
|**Представления** коллекции|**Представления** не поддерживается.|  
|**Процедуры** коллекции|**Append** и **удалить** методы не поддерживаются.|  
|**Процедура** объекта|**Команда** свойство не поддерживается.|  
|**Ключи** коллекции|**Append** и **удалить** методы не поддерживаются.|  
|**Пользователи** коллекции|**Пользователи** не поддерживается.|  
|**Группы** коллекции|**Группы** не поддерживается.|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Поставщик Microsoft OLE DB для ODBC  
  
|Объект или коллекция|Ограничение использования|  
|--------------------------|-----------------------|  
|**Каталог** объекта|**Создать** метод не поддерживается.|  
|**Таблицы** коллекции|**Append** и **удалить** методы не поддерживаются. Свойства доступны для чтения/записи до создания объекта и только для чтения при ссылке на существующий объект.|  
|**Процедуры** коллекции|**Append** и **удалить** методы не поддерживаются.|  
|**Процедура** объекта|**Команда** свойство не поддерживается.|  
|**Индексы** коллекции|**Append** и **удалить** методы не поддерживаются.|  
|**Ключи** коллекции|**Append** и **удалить** методы не поддерживаются.|  
|**Пользователи** коллекции|**Пользователи** не поддерживается.|  
|**Группы** коллекции|**Группы** не поддерживается.|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Поставщик OLE DB для Oracle (Microsoft)  
  
|Объект или коллекция|Ограничение использования|  
|--------------------------|-----------------------|  
|**Каталог** объекта|**Создать** метод не поддерживается.|  
|**Таблицы** коллекции|**Append** и **удалить** методы не поддерживаются. Свойства доступны для чтения/записи до создания объекта и только для чтения при ссылке на существующий объект.|  
|**Представления** коллекции|**Append** и **удалить** методы не поддерживаются.|  
|**Представление** объекта|**Команда** свойство не поддерживается.|  
|**Процедуры** объекта|**Append** и **удалить** методы не поддерживаются.|  
|**Процедура** объекта|**Команда** свойство не поддерживается.|  
|**Индексы** коллекции|**Append** и **удалить** методы не поддерживаются.|  
|**Ключи** коллекции|**Append** и **удалить** методы не поддерживаются.|  
|**Пользователи** коллекции|**Пользователи** не поддерживается.|  
|**Группы** коллекции|**Группы** не поддерживается.|