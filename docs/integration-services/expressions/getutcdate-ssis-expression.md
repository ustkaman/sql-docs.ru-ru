---
title: GETUTCDATE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5d3a437962aa2abc31103f6677781fb1d8ea73fe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE (выражение служб SSIS)
  Возвращает текущую дату системы в формате времени UTC (универсальное время, или время по Гринвичу), используя формат DT_DBTIMESTAMP. Функция GETUTCDATE не имеет аргументов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>Аргументы  
 None  
  
## <a name="result-types"></a>Типы результата  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример возвращает год текущей даты времени в формате UTC.  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 Этот пример возвращает количество дней между датой в столбце **ModifiedDate** и текущей датой в формате UTC.  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 Этот пример добавляет три месяца к текущей дате в формате UTC.  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a>См. также:  
 [GETDATE (выражение служб SSIS)](../../integration-services/expressions/getdate-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
