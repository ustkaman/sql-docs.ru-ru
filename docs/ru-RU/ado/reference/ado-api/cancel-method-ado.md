---
title: Cancel-метод (ADO) | Документы Microsoft
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
apitype: COM
f1_keywords:
- Recordset20::Cancel
- _Record::Cancel
- _Connection::Cancel
- Command25::Cancel
- _Stream::Cancel
helpviewer_keywords:
- Cancel method [ADO]
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5166578eb3ecb45c90e32ab2d3e447d8a0533b5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="cancel-method-ado"></a>Метод Cancel (ADO)
Отменяет выполнение вызова асинхронного метода, ожидающих утверждения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>Замечания  
 Используйте **отменить** метод для завершения выполнения асинхронного вызова метода: то есть метод вызван с **adAsyncConnect**, **adAsyncExecute**, или **adAsyncFetch** параметр.  
  
 В следующей таблице показано, какие задачи завершаются при использовании **отменить** метод для конкретного типа объектов.  
  
|Если *объекта* —|Последний асинхронный вызов этого метода завершается|  
|----------------------|-------------------------------------------------------------|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|[Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Соединение](../../../ado/reference/ado-api/connection-object-ado.md)|[Выполнение](../../../ado/reference/ado-api/execute-method-ado-connection.md) или [Open](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[Запись](../../../ado/reference/ado-api/record-object-ado.md)|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), [макрокоманду УдалитьЗапись](../../../ado/reference/ado-api/deleterecord-method-ado.md), [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md), или [Open](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Набор записей](../../../ado/reference/ado-api/recordset-object-ado.md)|[Открытие](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Поток](../../../ado/reference/ado-api/stream-object-ado.md)|[Открытие](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>См. также  
 [Пример метода Cancel (Visual Basic)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [Пример метода Cancel (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Пример метода Cancel (VC ++)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Метод Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Выполнить метод (команда ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Выполнить метод (соединение ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Метод Open (соединение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)
