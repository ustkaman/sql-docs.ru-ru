---
title: sys.soap_endpoints (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- soap_endpoints_TSQL
- sys.soap_endpoints
- soap_endpoints
- sys.soap_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.soap_endpoints catalog view
ms.assetid: f50dcbfc-02ed-4a19-9c07-c78a5a1b3224
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 7f3af00bccbef87dd6390c5421b8d625e4b6ed42
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="syssoapendpoints-transact-sql"></a>sys.soap_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Содержит по одной строке для каждой конечной точки на сервере, которая содержит полезные данные типа SOAP. Для каждой строки в данном представлении имеется соответствующая строка с тем же **endpoint_id** в **sys.http_endpoints** каталога представление, которое содержит метаданные конфигурации HTTP.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**< унаследованные столбцы >**||Список столбцов, наследуемых этим представлением см. в разделе [sys.endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**is_sql_language_enabled**|**бит**|1 = BATCHES = ENABLED означает, что нерегламентированные пакеты SQL допустимы для конечной точки.|  
|**wsdl_generator_procedure**|**nvarchar(776)**|Трехкомпонентное имя хранимой процедуры, которая реализует этот метод.<br /><br /> Для имен методов требуется использовать трехкомпонентные имена. Имена из одного, двух или четырех компонентов недопустимы.|  
|**default_database**|**sysname**|Имя базы данных по умолчанию, заданное в параметре DATABASE.<br /><br /> NULL = указан параметр DEFAULT.|  
|**default_namespace**|**nvarchar(384)**|Пространство имен по умолчанию, заданные в пространстве ИМЕН = параметр, или "http://tempuri.org", если вместо него указан параметр DEFAULT.|  
|**default_result_schema**|**tinyint**|Значение по умолчанию для параметра SCHEMA:<br /><br /> 0 = нет<br /><br /> 1 = STANDARD|  
|**default_result_schema_desc**|**nvarchar(60)**|Описание значения по умолчанию параметра SCHEMA:<br /><br /> None<br /><br /> STANDARD|  
|**is_xml_charset_enforced**|**бит**|0 = указан параметр CHARACTER_SET = SQL.<br /><br /> 1 = указан параметр CHARACTER_SET = XML.|  
|**is_session_enabled**|**бит**|0 = указан параметр SESSION = DISABLE.<br /><br /> 1 = указан параметр SESSION = ENABLED.|  
|**session_timeout**|**int**|Значение, указанное параметром SESSION_TIMEOUT.|  
|**login_type**|**nvarchar(60)**|Тип проверки подлинности, допустимый для этой конечной точки:<br /><br /> WINDOWS<br /><br /> MIXED|  
|**header_limit**|**int**|Максимально допустимый размер заголовка SOAP.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога конечных точек (Transact-SQL)](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
