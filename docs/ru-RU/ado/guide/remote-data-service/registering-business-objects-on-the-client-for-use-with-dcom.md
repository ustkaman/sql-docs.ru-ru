---
title: Регистрация бизнес-объектов на стороне клиента для использования в DCOM | Документы Microsoft
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
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 550bea8668a3420271ec4b1181c05e0b83b32c77
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>Регистрация бизнес-объектов на стороне клиента для использования в DCOM
Настраиваемые бизнес-объекты должны убедиться, что на стороне клиента можно сопоставить их имя программы (ProgId) с кодом CLSID, который может использоваться через DCOM. По этой причине идентификатор ProgID объекта DCOM должно быть в реестре клиентского и сопоставить с Идентификатором класса серверных бизнес-объекта. Для других поддерживаемых протоколов (HTTP, HTTPS и в процессе) это не требуется.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Например если предоставляют серверную бизнес-объект, вызывается MyBObj с Идентификатором определенного класса, например, «{00112233-4455-6677-8899-00AABBCCDDEE}», убедитесь, что добавлены следующие записи в реестр на стороне клиента:  
  
```  
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


