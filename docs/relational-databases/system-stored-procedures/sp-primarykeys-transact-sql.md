---
title: sp_primarykeys (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_primarykeys_TSQL
- sp_primarykeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_primarykeys
ms.assetid: 0f76dd31-5b7b-4209-9e2e-b9ed5cac164d
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 4377ac2958a2c5e1f00cf83985f6730d8194e6b9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spprimarykeys-transact-sql"></a>sp_primarykeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает столбцы первичных ключей для указанной удаленной таблицы по одной строке на ключевой столбец.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_primarykeys [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@table_server =** ] **"*** table_server"*  
 Имя связанного сервера, с которого возвращаются сведения о первичном ключе. *table_server* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@table_name =** ] **"***table_name***"**  
 Имя таблицы, для которой возвращаются сведения о первичном ключе. *имя_таблицы*— **sysname**, значение по умолчанию NULL.  
  
 [  **@table_schema =** ] **"***table_schema***"**  
 Схема таблицы. *table_schema* — **sysname**, значение по умолчанию NULL. В среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соответствует владельцу таблицы.  
  
 [  **@table_catalog =** ] **"***значениям table_catalog***"**  
 Имя каталога, в котором указанный *table_name* находится. В среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соответствует имени базы данных. *значениям table_catalog* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Каталог таблицы.|  
|**ПО ЗНАЧЕНИЯМ TABLE_SCHEM**|**sysname**|Схема таблицы.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя таблицы.|  
|**COLUMN_NAME**|**sysname**|Имя столбца.|  
|**KEY_SEQ**|**int**|Порядковый номер столбца в первичном ключе, состоящем из нескольких столбцов.|  
|**PK_NAME**|**sysname**|Идентификатор первичного ключа. Возвращает NULL, если не применим к источнику данных.|  
  
## <a name="remarks"></a>Замечания  
 **sp_primarykeys** выполняется путем запроса набор строк PRIMARY_KEYS **IDBSchemaRowset** интерфейса поставщика OLE DB, соответствующий *table_server*. *Table_name*, *table_schema*, *значениям table_catalog*, и *столбца* параметры передаются этому интерфейсу для ограничения строк возвращается.  
  
 **sp_primarykeys** возвращает пустой результирующий набор, если поставщик OLE DB указанного связанного сервера не поддерживает набор строк PRIMARY_KEYS **IDBSchemaRowset** интерфейса.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере с сервера `LONDON1` возвращаются первичные ключевые столбцы для таблицы `HumanResources.JobCandidate` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_primarykeys @table_server = N'LONDON1',   
   @table_name = N'JobCandidate',  
   @table_catalog = N'AdventureWorks2012',   
   @table_schema = N'HumanResources';  
```  
  
## <a name="see-also"></a>См. также  
 [Распределенные запросы хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
