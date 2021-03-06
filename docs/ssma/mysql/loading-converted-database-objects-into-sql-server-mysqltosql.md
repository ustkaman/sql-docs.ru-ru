---
title: Загрузка преобразованных объектов базы данных, в SQL Server (MySQLToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ac993a6d-0283-4823-8793-6b217677dfa3
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 3d96528033ab2f852be1e91e64efdda77eb3807a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="loading-converted-database-objects-into-sql-server-mysqltosql"></a>Загрузка преобразованных объектов базы данных, в SQL Server (MySQLToSQL)
После преобразования базы данных MySQL для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, вы можете загрузить полученные объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Можно иметь SSMA создания объектов, или можно внести в скрипт объекты и запускать скрипты самостоятельно. Кроме того, SSMA позволяет заменить метаданные целевой фактическое содержимое [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Выбор между синхронизации и сценарии  
Если вы хотите загрузить объекты преобразованную базу данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure без изменений, может иметь SSMA непосредственного создания или повторного создания объектов базы данных. Метод выполняется быстро и просто, что не позволяет настраивать код Transact-SQL, определяющий [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объектов SQL Azure.  
  
Если вы хотите изменить Transact-SQL, используемый для создания объектов или если требуется больший контроль над создания объектов, используйте SSMA для создания скриптов. Затем изменить эти сценарии, создайте каждый объект отдельно и даже использовать агент SQL Server для планирования, создания этих объектов.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>С помощью SSMA для синхронизации объектов с SQL Server  
Чтобы использовать SSMA для создания объектов базы данных SQL Server или SQL Azure, выберите объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure, а затем синхронизировать объекты с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, как показано в следующей процедуре. По умолчанию, если объекты, уже существующие в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure и если SSMA метаданных имеет некоторые локальные изменения или обновления определения этих объектов очень, то SSMA приведут к изменению определения объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Поведение по умолчанию можно изменить путем редактирования **параметры проекта**.  
  
> [!NOTE]  
> Можно выбрать существующий [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объекты базы данных SQL Azure, которые не были преобразованы из базы данных MySQL. Тем не менее эти объекты не будет повторно или изменен с SSMA.  
  
##### <a name="to-synchronize-objects-with-sql-server-or-sql-azure"></a>Для синхронизации объектов с SQL Server или SQL Azure  
  
1.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure, разверните в верхней [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или узел SQL Azure, а затем разверните **баз данных**.  
  
2.  Выберите объекты для обработки:  
  
    -   Чтобы синхронизировать всей базы данных, установите флажок рядом с именем базы данных.  
  
    -   Чтобы синхронизировать или исключить отдельные объекты или категории объектов, установите или снимите флажок рядом с объекту или папке.  
  
3.  После выбора объектов для обработки в SQL Server или обозреватель метаданных SQL Azure, щелкните правой кнопкой мыши **баз данных**, а затем нажмите кнопку **синхронизации с базой данных**.  
  
    Вы также можете синхронизировать отдельных объектов и категории объектов, щелкните правой кнопкой мыши объект или ее родительскую папку, выберите команду **синхронизации с базой данных**.  
  
    После этого будет отображаться SSMA **синхронизации с базой данных** диалоговое окно, в котором имеются две группы элементов. На левой стороне SSMA показывает выбранные объекты базы данных представлены в дереве. С правой стороны появится дерево, представляющее те же объекты в метаданных SSMA. Вы можете разверните дерево, щелкнув вправо или влево кнопку «+». Направление синхронизации отображается в столбце действий, который располагается между двумя деревьев.  
  
    Знак действие может находиться в трех состояний:  
  
    -   Стрелка влево означает, что содержимое метаданные сохраняются в базе данных (по умолчанию).  
  
    -   Стрелка вправо означает, что содержимое базы данных перезапишет SSMA метаданных.  
  
    -   Знак перекрестного означает, что будет выполнено никаких действий.  
  
    -   Щелкните знак «действие» для изменения состояния. Фактический синхронизация будет выполняться при нажатии кнопки **ОК** кнопки **синхронизации с базой данных** диалогового окна.  
  
## <a name="scripting-objects"></a>Создание скриптов для объектов  
Чтобы сохранить [!INCLUDE[tsql](../../includes/tsql_md.md)] определений объектов преобразованную базу данных, или для изменения определения объектов и самостоятельно выполнять скрипты можно сохранить ее определения объектов, [!INCLUDE[tsql](../../includes/tsql_md.md)] сценариев.  
  
**Для сохранения объектов в виде скриптов**  
  
1.  После выбора объектов для сохранения скрипта, щелкните правой кнопкой мыши **баз данных**, а затем нажмите кнопку **Сохранение скрипта**.  
  
    Можно также создать скрипт отдельных объектов и категории объектов, щелкнув правой кнопкой мыши объект или ее родительскую папку, выберите команду **Сохранение скрипта**.  
  
2.  В **Сохранить как** диалогового окна найдите папку, в которой вы хотите сохранить скрипт, введите имя файла в **имя файла** поле, а затем [!INCLUDE[clickOK](../../includes/clickok_md.md)] SSMA добавит .sql расширение имени файла.  
  
### <a name="modifying-scripts"></a>Изменение скриптов  
После сохранения SQL Server или SQL Azure определения объектов как сценарий SQL Server Management Studio можно использовать для его изменения.  
  
**Изменение сценария**  
  
1.  В среде Management Studio **файл** последовательно выберите пункты **откройте**, а затем нажмите кнопку **файл**.  
  
2.  В открытом диалоговом окне, найдите и выберите файл сценария и нажмите кнопку **ОК**.  
  
3.  Измените файл скрипта с помощью редактора запросов. Дополнительные сведения о редакторе запросов см. в разделе «Редактор удобных команд и компоненты» в электронной документации по SQL Server.  
  
4.  Чтобы сохранить скрипт, в меню файл, выберите **Сохранить**.  
  
### <a name="running-scripts"></a>Выполнение сценариев  
Можно запустить сценарий или отдельных инструкций в SQL Server Management Studio.  
  
**Для выполнения сценария**  
  
1.  В SQL Server Management Studio **файл** последовательно выберите пункты **откройте** и нажмите кнопку **файл**.  
  
2.  В открытом диалоговом окне, найдите и выберите файл сценария и нажмите кнопку **ОК**.  
  
3.  Чтобы выполнить полный сценарий, нажмите клавишу **F5** ключа.  
  
4.  Чтобы выполнить набор инструкций, инструкции select, в окне редактора запросов и нажмите клавишу **F5** ключа.  
  
5.  Дополнительные сведения о том, как использовать редактор запросов для выполнения скриптов в разделе «Запрос SQL Server Management Studio Transact-SQL» в электронной документации по SQL Server.  
  
6.  Можно также выполнять скрипты из командной строки с помощью **sqlcmd** служебной программы и от агента SQL Server. Дополнительные сведения о **sqlcmd**, в разделе «программа sqlcmd» в электронной документации по SQL Server. Дополнительные сведения об агенте SQL Server см. в разделе «Автоматизация административных задач (агент SQL Server)» электронной документации по SQL Server.  
  
## <a name="securing-objects-in-sql-server"></a>Защита объектов в SQL Server  
После загрузки объектов преобразованную базу данных в SQL Server можно grant и deny разрешения на эти объекты. Рекомендуется сделать это перед выполнением переноса данных в SQL Server. Сведения о том, как обеспечить безопасность объектов в SQL Server см. в разделе «Безопасность вопросы для баз данных и базы данных приложений» в электронной документации по SQL Server.  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом в процессе миграции является [переноса данных MySQL в SQL Server — база данных SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
## <a name="see-also"></a>См. также  
[Миграция MySQL баз данных SQL Server — Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
