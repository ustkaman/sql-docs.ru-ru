---
title: sp_addextendedproc (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addextendedproc_TSQL
- sp_addextendedproc
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addextendedproc
ms.assetid: c0d4b47b-a855-451e-90e5-5fb2d836ebfa
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2083d370479fa19049a083ef401574f21740929c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spaddextendedproc-transact-sql"></a>sp_addextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Регистрирует имя новой расширенной хранимой процедуры [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте вместо этого [интеграцию со средой CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addextendedproc [ @functname = ] 'procedure' ,   
     [ @dllname = ] 'dll'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@functname =** ] **"***процедура***"**  
 Имя функции, вызываемой из динамически подключаемой библиотеки (DLL). *процедура* — **nvarchar(517)**, не имеет значения по умолчанию. *процедура* может также включать имя владельца в форме *owner.function*.  
  
 [  **@dllname =** ] **"***dll***"**  
 Имя DLL, в которой содержится функция. *библиотеки DLL* — **varchar(255)**, не имеет значения по умолчанию. Рекомендуется указывать полный путь DLL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 После создания расширенной хранимой процедуры, его необходимо добавить к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью **sp_addextendedproc**. Дополнительные сведения см. в разделе [Добавление расширенную хранимую процедуру SQL Server](../../relational-databases/extended-stored-procedures-programming/adding-an-extended-stored-procedure-to-sql-server.md).  
  
 Эта процедура может быть запущена только в **master** базы данных. Для выполнения расширенной хранимой процедуры из базы данных, отличный от **master**, используйте в имени расширенной хранимой процедуры с **master**.  
  
 **sp_addextendedproc** добавляет записи [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) представления каталога, регистрация имени новой расширенной хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Он также добавляет запись в [sys.extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) представления каталога.  
  
> [!IMPORTANT]  
>  Существующие DLL-библиотеки, которые зарегистрированы без указания полного пути, перестанут работать после обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Чтобы устранить проблему, используйте **sp_dropextendedproc** для отмены регистрации библиотеки DLL, а затем зарегистрируйте его с **sp_addextendedproc**, указав полный путь.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_addextendedproc**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере добавляется **xp_hello** расширенной хранимой процедуры.  
  
```  
USE master;  
GO  
EXEC sp_addextendedproc xp_hello, 'c:\xp_hello.dll';  
```  
  
## <a name="see-also"></a>См. также  
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
