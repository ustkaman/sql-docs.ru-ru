---
title: Подключение к источникам данных | Документы Microsoft
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
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 706f340ca60799cc9aa8fb745f031e1c68cc34dc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-data-sources"></a>Подключение к источникам данных
ADO **подключения** представляет уникальный сеанс с источником данных, включая СУБД, хранилище файла или файл с разделителями-запятыми. В случае система клиент сервер базы данных соединение ADO может быть действительное сетевое подключение к серверу.  
  
 **Подключения** объект поддерживает различные [свойства и методы](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md) для указания конфигурации соединения, открытие и закрытие соединений, создания и выполнения команд в источнике данных и предоставляет сведения о проектировании базового источника данных в виде наборов строк схемы, и т. д. В зависимости от функциональных возможностей, поддерживаемых поставщика, некоторые коллекции, методы или свойства **подключения** могут оказаться недоступными.  
  
 Можно подключиться к источнику данных с помощью **подключения** объекта или с помощью **записей** объекта.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование объекта Connection](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [Использование объекта Recordset](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [Создание строки подключения](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [Указание свойств подключения](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [Управление транзакциями](../../../ado/guide/data/controlling-transactions-ado.md)
