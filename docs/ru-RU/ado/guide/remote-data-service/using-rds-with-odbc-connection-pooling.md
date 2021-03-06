---
title: Использование служб удаленных рабочих СТОЛОВ с соединением ODBC пулов | Документы Microsoft
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
- connection pooling in RDS [ADO]
ms.assetid: e8b912c1-da5b-4e85-a000-1e6648a94237
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e304952f12102d415a9ba4722b10b654058693aa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-rds-with-odbc-connection-pooling"></a>Использование служб удаленных рабочих СТОЛОВ с соединением ODBC пулов
При использовании источника данных ODBC можно использовать параметр в Internet Information Services (IIS) пула подключений для достижения высокой производительности обработки рабочей нагрузки. Организация пулов соединений является обслуживание открытом состоянии для часто используемых подключений диспетчера ресурсов для подключений.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Для включения пула подключений, обратитесь к документации служб IIS.  
  
 Обратите внимание на то, что включение пулов соединений может повлечь веб-сервера на другие ограничения, как указано в документации по Microsoft Internet Information Services.  
  
 Чтобы организация пулов соединений стабильна и обеспечивает повышение производительности, необходимо настроить Microsoft SQL Server для использования сетевой библиотеки сокет TCP/IP.  
  
 Чтобы сделать это, необходимо:  
  
-   Настройка компьютера SQL Server, чтобы использовать сокеты TCP/IP.  
  
-   Настройка веб-сервера для использования сокетов TCP/IP.  
  
## <a name="configuring-the-sql-server-computer-to-use-tcpip-sockets"></a>Настройка компьютера SQL Server, чтобы использовать сокеты TCP/IP  
 На компьютере SQL Server запустите программу установки SQL Server, чтобы взаимодействие с источником данных использовать сетевую библиотеку сокетов TCP/IP.  
  
### <a name="to-specify-the-tcpip-socket-network-library-on-the-sql-server-computer"></a>Чтобы указать сетевую библиотеку сокетов TCP/IP на компьютере SQL Server  
  
### <a name="in-microsoft-sql-server-65"></a>В Microsoft SQL Server 6.5.  
  
1.  Из меню «Пуск» выберите пункт программы, пункты Microsoft SQL Server 6.5 и нажмите кнопку установки SQL.  
  
2.  Дважды нажмите кнопку Продолжить.  
  
3.  В Microsoft SQL Server — диалоговое окно «Параметры», выберите сетевую поддержку изменения и нажмите кнопку Продолжить.  
  
4.  Убедитесь, что установлен флажок сокеты TCP/IP и нажмите кнопку ОК.  
  
5.  Нажмите кнопку Продолжить для завершения и выйти из программы установки.  
  
### <a name="in-microsoft-sql-server-70"></a>В Microsoft SQL Server 7.0:  
  
1.  Из меню «Пуск» выберите пункт программы, выберите Microsoft SQL Server 7.0 и нажмите кнопку Server Network Utility.  
  
2.  На вкладке «Общие» диалогового окна нажмите кнопку "Добавить".  
  
3.  В диалоговом окне Добавление конфигурации сетевой библиотеки выберите TCP/IP.  
  
4.  В полях адрес прокси-сервера и номер порта введите адрес порта номер и прокси-сервера, предоставляемые администратором сети.  
  
5.  Нажмите кнопку ОК, чтобы завершить и выйти из программы установки.  
  
## <a name="configuring-the-web-server-to-use-tcpip-sockets"></a>Настройка веб-сервера для использования сокетов TCP/IP  
 Существует два варианта для настройки веб-сервера для использования сокетов TCP/IP. Возможностях зависит от того, является ли все серверы SQL Server осуществляется с веб-сервера или получить доступ к определенной SQL Server с веб-сервера.  
  
 Если все серверы SQL Server осуществляется на веб-сервере, необходимо запустить служебную программу SQL Server клиента конфигурации на компьютере веб-сервера. Следующие шаги изменить сетевую библиотеку по умолчанию для всех подключений SQL Server, сделанных этой веб-сервера IIS для использования сетевой библиотеки сокеты TCP/IP.  
  
### <a name="to-configure-the-web-server-all-sql-servers"></a>Чтобы настроить веб-сервер (все серверы SQL Server)  
  
### <a name="for-microsoft-sql-server-65"></a>Для Microsoft SQL Server 6.5.  
  
1.  Из меню «Пуск» выберите пункт программы, выберите Microsoft SQL Server 6.5 и нажмите кнопку средства настройки клиента SQL.  
  
2.  Перейдите на вкладку Сетевая библиотека.  
  
3.  В поле по умолчанию сети выберите сокеты TCP/IP.  
  
4.  Нажмите кнопку Готово, чтобы сохранить изменения и выйдите из программы.  
  
### <a name="for-microsoft-sql-server-70"></a>Для Microsoft SQL Server 7.0:  
  
1.  Из меню «Пуск» выберите пункт программы, выберите Microsoft SQL Server 7.0 и нажмите кнопку Client Network Utility.  
  
2.  Перейдите на вкладку Общие.  
  
3.  В поле по умолчанию сетевой библиотеки выберите TCP/IP.  
  
4.  Нажмите кнопку ОК, чтобы сохранить изменения и выйдите из программы.  
  
 Если указанный сервер SQL осуществляется на веб-сервере, необходимо запустить SQL Server Client Configuration Utility на компьютере веб-сервера. Чтобы изменить сетевой библиотеки для определенного подключения SQL Server, настройте программное обеспечение клиента SQL Server на компьютере веб-сервера следующим образом.  
  
### <a name="to-configure-the-web-server-a-specific-sql-server"></a>Чтобы настроить веб-сервер (конкретных SQL Server)  
  
### <a name="for-microsoft-sql-server-65"></a>Для Microsoft SQL Server 6.5.  
  
1.  Из меню «Пуск» выберите пункт программы, выберите Microsoft SQL Server 6.5 и нажмите кнопку средства настройки клиента SQL.  
  
2.  Щелкните вкладку "Дополнительно".  
  
3.  В диалоговом окне сервера введите имя сервера для подключения с помощью сокетов TCP/IP.  
  
4.  В поле имя DLL-файла выберите сокеты TCP/IP.  
  
5.  Нажмите кнопку Добавить или изменить. Все источники данных, указывающих на этот сервер теперь будут использовать сокеты TCP/IP.  
  
6.  Нажмите кнопку Готово.  
  
### <a name="for-microsoft-sql-server-70"></a>Для Microsoft SQL Server 7.0:  
  
1.  Из меню «Пуск» выберите пункт программы, выберите Microsoft SQL Server 7.0 и нажмите кнопку средства настройки клиента.  
  
2.  Перейдите на вкладку Общие.  
  
3.  Нажмите кнопку «Добавить».  
  
4.  Введите псевдоним сервера в поле псевдоним сервера. В поле сетевой библиотеки выберите TCP/IP. В поле "имя компьютера" введите имя компьютера сервера, на котором осуществляет прослушивание клиентов сокетов TCP/IP. В поле номера порта введите порт, прослушиваемый SQL Server.  
  
5.  Нажмите кнопку ОК и нажмите ОК еще раз, чтобы выйти из программы.  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)






















