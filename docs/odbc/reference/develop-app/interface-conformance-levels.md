---
title: Интерфейс уровни соответствия | Документы Microsoft
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
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 2c470e54-0600-4b2b-b1f3-9885cb28a01a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 890684bf513b80cd484f7b15c75a04c38553513b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="interface-conformance-levels"></a>Уровни согласованности интерфейса
Выравнивание предназначено для уведомления приложения, какие функции доступны на него с помощью драйвера. Схема распределения, основаны на функциях не достаточно достижения этой цели. В ODBC 3. *x*, драйверы классифицируются в зависимости от возможностей, они имеют. Поддержка функции можно включить поддержка функции; Оно также может включать поле дескриптора, атрибут инструкции, значение «Y» поддержка типа данных, возвращенных **SQLGetInfo**, и т. д.  
  
 Чтобы упростить спецификации интерфейса соответствия, ODBC определяет три уровня совместимости. Для достижения соответствия определенного уровня, драйвер должен удовлетворять всем требованиям, уровень соответствия. Совместимость с данного уровня означает полное соответствие со всех более низких уровней.  
  
 Уровни согласованности не всегда разделить аккуратно поддержки перечень функций ODBC, но укажите поддерживаемые функции, перечисленные в следующих разделах. Для предоставления поддержки для компонента, драйвер должен поддерживать некоторые или все виды вызовы некоторых функций ODBC (Дополнительные сведения см. в разделе [функции соответствия](../../../odbc/reference/develop-app/function-conformance.md)), установка определенных атрибутов (см. [соответствия атрибута ](../../../odbc/reference/develop-app/attribute-conformance.md)) и некоторые поля дескриптора (см. [дескриптора поля соответствия](../../../odbc/reference/develop-app/descriptor-field-conformance.md)).  
  
 Приложение обнаруживает уровень соответствия интерфейса драйвера, соединение с источником данных и вызвав **SQLGetInfo** с параметром SQL_ODBC_INTERFACE_CONFORMANCE.  
  
 Драйверы могут реализовать функции выше уровня, к которому они утверждения полного соответствия. Приложениям обнаруживать такие дополнительные возможности, вызвав **SQLGetFunctions** (чтобы определить, какие функции ODBC присутствуют) и **SQLGetInfo** (для запроса различных других возможностей ODBC).  
  
 Существует три уровня соответствия интерфейс ODBC: ядер, уровень 1 и уровень 2.  
  
> [!NOTE]  
>  Эти уровни соответствия имеют различные требования, чем уровни соответствия ODBC API с тем же именем в ODBC 2 *.x*. В частности, все функции содержится в разрешении ODBC 2 *.x* интерфейса API ODBC уровня 1 теперь являются частью уровень соответствия основной интерфейс. В результате многие драйверы ODBC могут сообщать соответствия интерфейс уровня ядра.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Соответствие основного интерфейса](../../../odbc/reference/develop-app/core-interface-conformance.md)  
  
-   [Соответствие интерфейса уровня 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md)  
  
-   [Соответствие интерфейса уровня 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md)  
  
-   [Соответствие функции](../../../odbc/reference/develop-app/function-conformance.md)  
  
-   [Соответствие атрибутов](../../../odbc/reference/develop-app/attribute-conformance.md)  
  
-   [Соответствие поля дескриптора](../../../odbc/reference/develop-app/descriptor-field-conformance.md)
