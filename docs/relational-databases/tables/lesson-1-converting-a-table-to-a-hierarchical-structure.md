---
title: Занятие 1. Преобразование таблицы в иерархическую структуру | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a38cbcec7f42ff99e0e7c56de16fc30a3187dded
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Урок 1. преобразование таблицы в иерархическую структуру
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Если у клиентов имеются таблицы, в которых для выражения иерархических связей используются самосоединения, то эти таблицы можно преобразовать в иерархическую структуру, руководствуясь указаниями из данного занятия. Миграция от старого метода представления к методу представления, использующему тип данных **hierarchyid**, проходит относительно легко. После миграции пользователи получат компактное и легкое для понимания иерархическое представление, которое может быть проиндексировано несколькими способами для обеспечения эффективного поиска.  
  
В этом занятии происходит изучение существующей таблицы, создание новой таблицы, содержащей столбец **hierarchyid** , заполнение этой таблицы данными из таблицы источника, а также проводится демонстрация трех стратегий индексирования. Это занятие содержит следующие разделы:  
  
-   [Изучение текущей структуры таблицы сотрудников](../../relational-databases/tables/lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [Заполнение таблицы существующими иерархическими данными](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Оптимизация таблицы NewOrg](../../relational-databases/tables/lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [Сводка. преобразование таблицы в иерархическую структуру](../../relational-databases/tables/lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>предварительные требования  
Для этого занятия требуется образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Изучение текущей структуры таблицы сотрудников](../../relational-databases/tables/lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>Следующее занятие  
[Занятие 2. Создание данных и управление ими в иерархической таблице](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
  
