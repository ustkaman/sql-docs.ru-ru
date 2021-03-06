---
title: Привести набор метаданных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 6d134515-e34d-4563-96d7-8ad7714818fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d309136c3682a781d4eef82e69e2a2f98a20efe2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="result-set-metadata"></a>Метаданные результирующего набора
*Метаданные* — это данные, описывающие другие данные. Например метаданные результирующего набора описывают результирующий набор, такие как число столбцов в результирующем наборе, типы данных этих столбцов, их имена, точность, допустимость значений NULL и т. д.  
  
 Взаимодействующие приложения следует всегда проверять метаданные столбцов результирующего набора. Метаданные столбца в результирующем наборе могут отличаться от метаданных для столбца, возвращаемым функцией каталога. Например предположим, что обновляемый столбец включен в результирующий набор, созданный путем соединения двух таблиц. Хотя **SQLColumnPrivileges** может указать, что пользователь может обновить столбец, метаданные результирующих наборов может не в том случае, если столбец находится на стороне «многие» соединения; обновить столбцов на стороне «один» соединения, но не на многие источники данных» сторона «многие». Даже типы данных не может предположить, что тем же, поскольку источник данных может продвинут тип данных при создании результирующего набора.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Как используются метаданные?](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol и SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)
