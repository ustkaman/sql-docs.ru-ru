---
title: Файл настроек журналы раздел | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- logs section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: a368e264-865c-41ee-be00-d9097255c2ea
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37bcfdea2c98295d2869cd4bc5766e89758e2773
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="customization-file-logs-section"></a>Раздел журналы настройки файла
**Журналы** раздел содержит записи файла журнала, который указывает имя файла, в который записываются ошибки во время работы **DataFactory**.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Запись файла журнала имеет следующую форму:  
  
```  
  
err=  
FileName  
  
```  
  
## <a name="remarks"></a>Замечания  
  
|Часть|Описание|  
|----------|-----------------|  
|**Err**|Строковый литерал, который указывает на это является запись в файле журнала.|  
|*FileName*|Полный путь и имя файла. Имя файла обычно **c:\msdfmap.log**.|  
  
 Файл журнала будет содержать имя пользователя, HRESULT, Дата и время каждой ошибки.  
  
## <a name="see-also"></a>См. также  
 [Файл настроек присоединения раздела](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Раздел SQL настройки файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Раздел UserList настройки файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Основные сведения о настройке файла](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


