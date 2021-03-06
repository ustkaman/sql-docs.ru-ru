---
title: Пакетная обработка вызовов хранимых процедур | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dbb2279b3a32fd2929a7e9e626a0481ea38fefd0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="batching-stored-procedure-calls"></a>Создание пакетной обработки вызовов хранимых процедур
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента автоматически создает пакеты вызовов хранимых процедур на сервер, когда это необходимо. Драйвер производит это действие только при использовании управляющей последовательности ODBC CALL и не производит его для инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE. Создание пакетов вызовов хранимых процедур может уменьшить количество обменов данных с сервером и значительно повысить производительность.  
  
 Драйвер создает пакеты вызовов процедур на сервере при выполнении пакета, который содержит несколько управляющих последовательностей ODBC CALL. Он также создает пакеты вызовов процедур, когда массивы связанных параметров используются с управляющей последовательностью ODBC CALL. Например, при использовании либо на уровне столбца или параметра привязка для связывания массива из пяти элементов с параметрами инструкции ODBC CALL SQL при **SQLExecute** или **SQLExecDirect** вызова драйвер отправляет один пакет с пятью вызовами процедур на сервер.  
  
## <a name="see-also"></a>См. также  
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
