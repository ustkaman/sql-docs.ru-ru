---
title: Установка собственного клиента SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
caps.latest.revision: 44
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d9343fa6edc83886a62d1e478d3c20d5c9f18c18
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="installing-sql-server-native-client"></a>Установка собственного клиента SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 > Содержимое, связанное с предыдущих версий SQL Server, в разделе [Установка собственного клиента SQL Server](https://msdn.microsoft.com/en-US/library/ms131321(SQL.120).aspx).

[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 устанавливается при установке [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]. 
 
 Нет не SQL Server 2016 Native Client. Дополнительные сведения см. в разделе [собственный клиент SQL Server](../../../relational-databases/native-client/sql-server-native-client.md). 
 
Также можно извлечь файл sqlncli.msi с веб-страницы пакета дополнительных компонентов SQL Server 2012. Чтобы загрузить последнюю версию SQL Server Native Client, перейдите в раздел [пакет дополнительных компонентов Microsoft® SQL Server® 2012](http://www.microsoft.com/en-us/download/confirmation.aspx?id=29065). Если в предыдущей версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] раньше, чем SQL Server 2012 также устанавливается на компьютере, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 будет установленных side-by-side с более ранней версии.  
  
 Файлы собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (sqlncli11.dll, sqlnclir11.rll и s11ch_sqlncli.chm) устанавливаются в следующий каталог.  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  Все необходимые настройки реестра для поставщика OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполняются в процессе установки.  
  
 Заголовочный файл и библиотека собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (sqlncli.h и sqlncli11.lib) устанавливаются в следующий каталог.  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 Помимо установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента как часть [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] установки, имеется также программы установки распространяемого пакета, называется sqlncli.msi, который можно найти на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] установочный диск в следующем расположении: `%CD%\Setup\`.  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно распространять в виде файла sqlncli.msi. При развертывании приложения может потребоваться установка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Один из способов установки нескольких пакетов в одном (с точки зрения пользователя) сеансе установки состоит в применении технологии построителей цепочек и загрузчиков. Дополнительные сведения см. в разделе [разработки пользовательского пакета загрузчика для Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=115667) и [Добавление настраиваемых необходимых компонентов](http://go.microsoft.com/fwlink/?LinkId=115668).  
  
 Версии файла sqlncli.msi для архитектур x64 и Itanium устанавливают и 64-разрядную версию, и 32-разрядную версию собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если приложение планируется использовать на платформе, отличной от той, на которой оно разрабатывалось, можно скачать из центра загрузки Майкрософт версии sqlncli.msi for x64, Itanium и x86.  
  
 При инициировании sqlncli.msi по умолчанию устанавливаются только компоненты клиентской части. Этими компонентами служат файлы, поддерживающие работу приложения, разработанного с помощью собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Чтобы установить также компоненты пакета SDK, укажите в командной строке `ADDLOCAL=All`. Например:  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>Автоматическая установка  
 При использовании параметров /passive, /qn, /qb или /qr программы msiexec необходимо также указать параметр IACCEPTSQLNCLILICENSETERMS=YES, тем самым явно подтверждая принятие условий соглашения конечного пользователя. Этот параметр указывается только прописными буквами.  
  
## <a name="uninstalling-sql-server-native-client"></a>Удаление SQL Server Native Client  
 Поскольку приложения, такие как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сервера и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] средства зависят от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, очень важно не удалять [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, пока не будут удалены все зависимые приложения. Чтобы предупредить пользователей о том, что ваше приложение зависит [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, использование параметра установки APPGUID в MSI-ФАЙЛЕ, следующим образом:  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 Значением, передаваемым в APPGUID, служит код продукта. Код продукта необходимо создать при использовании установщика (Майкрософт) для формирования пакета установки приложения.  
  
## <a name="see-also"></a>См. также  
 [Построение приложений с использованием собственного клиента SQL Server](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [Инструкции по установке](http://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  
