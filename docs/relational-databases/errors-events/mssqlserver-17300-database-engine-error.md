---
title: MSSQLSERVER_17300 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17300 (Database Engine error)
ms.assetid: c1d6bfb6-28af-4df6-8087-25807602d282
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 471156345c294b8ee6a6e446273eae923e19bb88
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17300"></a>MSSQLSERVER_17300
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17300|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PROC_OUT_OF_SYSTASK_SESSIONS|  
|Текст сообщения|SQL Server не удалось запустить новую системную задачу либо из-за недостатка памяти, либо из-за превышения заданного в конфигурации максимального числа сеансов, допустимого для сервера. Проверьте, что на сервере достаточно памяти. Используйте хранимую процедуру sp_configure с параметром «user connections», чтобы выяснить максимально допустимое число соединений пользователя. Текущее число сеансов, включая пользовательские процессы, можно получить из представления sys.dm_exec_sessions.|  
  
## <a name="explanation"></a>Объяснение  
Не удалось запустить новую системную задачу либо из-за недостатка памяти, либо из-за превышения заданного в конфигурации числа сеансов для сервера.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте, что на сервере достаточно памяти. Проверьте текущее число системных задач с помощью представления sys.dm_exec_sessions и проверьте заданное значение максимального числа соединений пользователя с помощью хранимой процедуры sp_configure.  
  
При необходимости выполните следующие действия.  
  
-   Добавьте память на сервер.  
  
-   Завершите один или несколько сеансов.  
  
-   Увеличьте максимально допустимое число одновременно подключенных пользователей на сервере.  
  
## <a name="see-also"></a>См. также:  
[sp_configure (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
[Параметры конфигурации сервера (SQL Server)](~/database-engine/configure-windows/server-configuration-options-sql-server.md)  
[sys.dm_exec_sessions (Transact-SQL)](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
[Настройка параметра конфигурации сервера user connections](~/database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md)  
[KILL (Transact-SQL)](~/t-sql/language-elements/kill-transact-sql.md)  
  
