---
title: SQLTables (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8eccd686c1c4e3226a929cb39ee16e1921435ca
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: 1 уровень  
  
 Возвращает список имен таблиц, указанный в параметре **SQLTables** инструкции. Если параметр не указан, возвращает имена таблиц, хранящихся в текущем источнике данных. Драйвер возвращает данные в виде результирующего набора.  
  
 Перечисления типа вызывает метод не получит запись результирующего набора для представления удаленного или локального параметризованных представлений. Тем не менее вызов **SQLTables** с уникальной таблицы описатель имя будет найти совпадения для такого представления, при его наличии с таким именем, это обеспечивает API-интерфейса, используемых для проверки конфликтов имен до создания новой таблицы.  
  
> [!NOTE]  
>  Драйвер Visual FoxPro ODBC различает [таблицы базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) и [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md), даже в том случае, если оба типа таблиц хранятся в том же каталоге, в вашей системе. Если источником данных является каталог свободных таблиц, драйвер ODBC для Visual FoxPro каталога или не возвращает имена всех таблиц, которые связаны с базой данных.  
  
 Дополнительные сведения см. в разделе [SQLTables](../../odbc/reference/syntax/sqltables-function.md) в *справочнике программиста ODBC*.
