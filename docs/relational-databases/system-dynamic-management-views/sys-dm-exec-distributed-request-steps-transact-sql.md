---
title: sys.dm_exec_distributed_request_steps (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_distributed_request_steps
- sys.dm_exec_distributed_request_steps management view
ms.assetid: 1954541d-b716-4e03-8fcc-7022f428e01d
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5f8f84a81771736fb44b1a424a677fa1de7984bf
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmexecdistributedrequeststeps-transact-sql"></a>sys.dm_exec_distributed_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех действиях, которые образуют указанного PolyBase запроса или запроса. Он содержит одну строку для каждого действия запроса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**int**|execution_id и step_index составляющие ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|КОД в разделе [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|Позиция этого шага в последовательности действий, составляющих запрос.|0 (n-1) для запроса с n шагов.|  
|operation_type|**nvarchar(128)**|Тип операции, представленное в этом действии.|«MoveOperation», «OnOperation», «RandomIDOperation», «RemoteOperation», «ReturnOperation», «ShuffleMoveOperation», «TempTablePropertiesOperation», «DropDiagnosticsNotifyOperation», «HadoopShuffleOperation», «HadoopBroadCastOperation» «HadoopRoundRobinOperation»|  
|distribution_type|**nvarchar(32)**|Где выполнении шага.|«AllComputeNodes «,» AllDistributions, «ComputeNode», «распространение», «AllNodes», «SubsetNodes», «SubsetDistributions,» не задано».|  
|значение параметра location_type действия|**nvarchar(32)**|Где выполнении шага.|«Вычисления», «Заголовок» или «DMS». Все действия перемещения данных показывают «DMS».|  
|status|**nvarchar(32)**|Состояние этого шага|«Ожидание» «Выполняется», «Завершено», «Сбой», «UndoFailed», «PendingCancel», «отменено», «Отменено», «Прервано»|  
|error_id|**nvarchar(36)**|Уникальный идентификатор, связанный с этим шагом, если таковые имеются ошибки|В разделе идентификатор [sys.dm_exec_compute_node_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), значение NULL, если не возникло ошибок.|  
|start_time|**datetime**|Время начала выполнения шага|Меньше или равно значению текущего времени и размером менее end_compile_time запроса, к которому принадлежит этот шаг.|  
|end_time|**datetime**|Время, по которому этот шаг завершил выполнение, была отменена или не удалось.|Меньше или равно значению текущего времени и размером менее start_time присваивается значение NULL для шагов, которые в настоящее время выполнения или в очереди.|  
|total_elapsed_time|**int**|Суммарное время действия запроса на выполнение, в миллисекундах|Между 0 и разницу между end_time и start_time. 0 для шаги в очереди.|  
|row_count|**bigint**|Общее число строк, измененных или возвращаемого этим запросом|0 для действия, которые не изменить или возвращают данные, число строк, затронутых в противном случае. Значение -1 для действия DMS.|  
|command|nvarchar(4000)|Содержит полный текст команды этого шага.|Любая строка допустимым запросом для шага. Если более 4000 символов усекаются.|  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
