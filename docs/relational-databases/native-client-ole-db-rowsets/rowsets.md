---
title: Наборы строк | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1d12a7c6dfc3a63d20a16a4a4361ffd46e4f8972
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="rowsets"></a>Наборы строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Набор строк — это несколько строк, содержащих столбцы данных. Наборы строк — это основные объекты, позволяющие всем поставщикам данных OLE DB представлять данные результирующих наборов в виде таблиц.  
  
 После создания сеанса с помощью **IDBCreateSession::CreateSession** метод, потребитель может использовать либо **IOpenRowset** или **IDBCreateCommand** интерфейс для сеанса, чтобы создать набор строк. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента поддерживает оба интерфейса. Оба эти метода описаны здесь.  
  
-   Создать набор строк путем вызова **IOpenRowset::OpenRowset** метод.  
  
     Это эквивалентно созданию набора строк из одной таблицы. Этот метод открывает и возвращает набор строк, включающий все строки одной базовой таблицы. Один из аргументов **OpenRowset** — идентификатор таблицы, который идентифицирует таблицу, из которой создается набор строк.  
  
-   Создать командный объект, вызвав **IDBCreateCommand::CreateCommand** метод.  
  
     Объект команд выполняет команды, поддерживаемые поставщиком. С помощью поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребитель может указать любую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)], например SELECT, или вызов хранимой процедуры. Создание набора строк с помощью объекта команд включает следующие шаги.  
  
    1.  Потребитель вызывает метод **IDBCreateCommand::CreateCommand** метод для сеанса, чтобы получить объект команд, запрашивающий **ICommandText** интерфейса на объект команды. Это **ICommandText** интерфейс задает и получает действительный текст команды. Потребитель заполняет текст команды путем вызова **ICommandText::SetCommandText** метод.  
  
    2.  Пользователь вызывает **ICommand::Execute** метод для команды. Объект набора строк, создаваемый во время выполнения команды, содержит результирующий набор этой команды.  
  
 Потребитель может использовать **ICommandProperties** интерфейс для получения или задания свойств набора строк, возвращаемого при выполнении команды по **ICommand::Execute** интерфейсов. Наиболее часто запрашиваемыми свойствами являются интерфейсы, которые должны поддерживаться набором строк. Кроме интерфейсов, потребитель может запросить свойства, изменяющие поведение набора строк или интерфейса.  
  
 Потребители освобождают наборы строк с **IRowset::Release** метод. При освобождении набора строк освобождаются все дескрипторы строк, удерживаемые потребителем для данного набора строк. При освобождении набора строк методы доступа не освобождаются. Если у вас есть **IAccessor** интерфейс, он по-прежнему имеет освобождается.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Создание набора строк с IOpenRowset](../../relational-databases/native-client-ole-db-rowsets/creating-a-rowset-with-iopenrowset.md)  
  
-   [Создание наборов строк с ICommand::Execute](../../relational-databases/native-client-ole-db-rowsets/creating-rowsets-with-icommand-execute.md)  
  
-   [Свойства набора строк и поведение](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
-   [Наборы строк и курсоры SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)  
  
-   [Выборка строк](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [Выборка одной строки при помощи интерфейса IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
-   [Закладки](../../relational-databases/native-client-ole-db-rowsets/bookmarks.md)  
  
-   [Обновление данных в наборах строк](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
