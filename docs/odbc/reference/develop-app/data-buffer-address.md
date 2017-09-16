---
title: "Адрес буфера данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7d57b8ec52324dd4bec320b6179507ab3102e629
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="data-buffer-address"></a>Адрес буфера данных
Приложение передает адрес буфера данных к драйверу в аргумент, часто с именем *ValuePtr* или же именем. Например, в вызове **SQLBindCol**, приложение указывает адрес *даты* переменной:  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Как упоминалось в [распределение и освобождение буферы](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) разделе адрес отложенное буфера должен оставаться действительным, пока буфер не связан.  
  
 Если он запрещен в частности адрес буфера данных могут быть указатель null. Для буферов, используемых для отправки данных к драйверу в результате драйвер пропустили информацию, как правило, содержащееся в буфере. Для буферов, используемых для получения данных от драйвера в результате драйверу не возвращать значение. В обоих случаях драйвер пропускает соответствующего аргумента длины буфера данных.