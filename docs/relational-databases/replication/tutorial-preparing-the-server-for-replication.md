---
title: Учебник. Подготовка SQL Server для репликации — издатель, распространитель, подписчик | Документы Майкрософт
ms.custom: ''
ms.date: 04/02/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1468095ba959f7baf383b68cfaab65dab2591af6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-prepare-sql-server-for-replication---publisher-distributor-subscriber"></a>Учебник. Подготовка SQL Server для репликации — издатель, распространитель, подписчик
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Перед тем, как настраивать топологию репликации, важно предусмотреть средства безопасности. В этом учебнике описывается, как лучше обезопасить топологию репликации и как настроить распространение, которое является первым шагом в репликации данных. В первую очередь необходимо пройти именно этот учебник.  
  
> [!NOTE]  
> Чтобы безопасно выполнять репликацию данных между серверами, следует выполнять все рекомендации, приведенные в разделе [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
В этом учебнике описывается, как подготовить сервер для безопасного выполнения репликации с минимальным числом привилегий.  

В этом учебнике рассматривается следующее.
> [!div class="checklist"]
> * Создание учетных записей Windows для репликации
> * Подготовка папки моментальных снимков
> * Настройка распространителя

## <a name="prerequisites"></a>предварительные требования
Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченный опыт работы с репликацией. 

Для работы с этим учебником в вашей системе должны быть установлены среда SQL Server Management Studio (SSMS) и следующие компоненты:  
  
-   На сервере-издателе (источник):  
  
    -   Любой выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кроме SQL Server Express или SQL Compact. Эти выпуски не могут быть издателями репликации.   
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] . В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются.  
  
-   На сервере-подписчике (целевом):  
  
    -   Любой выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], за исключением [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] не может быть подписчиком в репликации транзакций.  
  
- Установите [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Скачайте [образцы баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Инструкции по восстановлению базы данных из копии в среде SSMS см. в разделе [Восстановление базы данных](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 
    
>[!NOTE]
> - Репликация не поддерживается на серверах SQL Server, которые отличаются друг от друга более чем на две версии. Дополнительные сведения см. в разделе [Поддерживаемые версии SQL в топологии репликации](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/).
> - В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]необходимо подключиться к издателю и подписчику с помощью имени входа, которое является членом предопределенной роли сервера **sysadmin** . Дополнительные сведения о роли sysadmin см. в разделе [Роли уровня сервера](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles).  


**Предполагаемое время для выполнения заданий данного учебника: 30 минут**
  
## <a name="create-windows-accounts-for-replication"></a>Создание учетных записей Windows для репликации
В этом разделе будут созданы учетные записи Windows для запуска агентов репликации. На локальном сервере будут созданы отдельные учетные записи Windows для следующих агентов:  
  
|Агент|Местоположение|Имя учетной записи|  
|---------|------------|----------------|  
|агент моментальных снимков|Издатель|<*имя_компьютера*>\repl_snapshot|  
|Агент чтения журнала.|Издатель|<*имя_компьютера*>\repl_logreader|  
|Агент распространителя|Издатель и подписчик|<*имя_компьютера*>\repl_distribution|  
|Агент слияния.|Издатель и подписчик|<*имя_компьютера*>\repl_merge|  
  
> [!NOTE]  
> В учебниках по репликации издатель и распространитель совместно используют один экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (NODE1\SQL2016), а подписчик размещается на удаленном экземпляре (NODE2\SQL2016). Издатель и подписчик могут совместно использовать один и тот же экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но это не является обязательным. Если издатель и подписчик совместно используют один и тот же экземпляр, то не требуется выполнять шаги по созданию учетных записей на подписчике.  

### <a name="create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>Создание локальных учетных записей Windows для агентов репликации на издателе
  
1.  Откройте в издателе оснастку **Управление компьютером** из папки **Администрирование** панели управления.  
  
2.  В оснастке **Служебные программы**разверните узел **Локальные пользователи и группы**.  
  
3.  Щелкните правой кнопкой мыши значок **Пользователи**, а затем выберите **Новый пользователь**.  
     
4.  Введите **repl_snapshot** в поле **Имя пользователя**, укажите пароль и другие необходимые сведения, а затем нажмите кнопку **Создать**, чтобы создать учетную запись repl_snapshot: 

       ![Новый пользователь](media/tutorial-preparing-the-server-for-replication/newuser.png)
  
5.  Повторите предыдущий шаг, чтобы создать учетные записи repl_logreader, repl_distribution и repl_merge:  
 
    ![Пользователи репликации](media/tutorial-preparing-the-server-for-replication/replusers.png)
  
6.  Выберите **Закрыть**.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>Создание локальных учетных записей Windows для агентов репликации на подписчике  
  
1.  Откройте в подписчике оснастку **Управление компьютером** из папки **Администрирование** панели управления.  
  
2.  В оснастке **Служебные программы**разверните узел **Локальные пользователи и группы**.  
  
3.  Щелкните правой кнопкой мыши значок **Пользователи**, а затем выберите **Новый пользователь**.  
  
4.  Введите **repl_distribution** в поле **Имя пользователя**, укажите пароль и другие необходимые сведения, затем нажмите **Создать**, чтобы создать учетную запись repl_distribution.  
  
5.  Повторите предыдущий шаг, чтобы создать учетную запись repl_merge.  
  
6.  Выберите **Закрыть**.  

**См. также**: [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)  

## <a name="prepare-the-snapshot-folder"></a>Подготовка папки моментальных снимков
В этом разделе вы научитесь настраивать папку моментальных снимков для создания и хранения моментального снимка публикации. 

### <a name="create-a-share-for-the-snapshot-folder-and-assign-permissions"></a>Создание ресурса для папки моментальных снимков и настройка разрешений  
  
1.  В проводнике Windows перейдите к папке данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Путь по умолчанию — «C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data».  
  
2.  Создайте папку с именем **repldata**.  
  
3.  Щелкните правой кнопкой мыши папку и выберите команду **Свойства**.  
  
    A. В диалоговом окне **Свойства repldata** на вкладке **Общий доступ** щелкните **Открыть общий доступ**.  
  
    Б. В диалоговом окне **Расширенная настройка общего доступа** выберите **Открыть общий доступ к этой папке** и затем **Разрешения**:  

       ![Общий доступ к данным репликации](media/tutorial-preparing-the-server-for-replication/repldata.png)

6.  В диалоговом окне **Разрешения для ресурса repldata** выберите **Добавить**. В текстовом поле **Выбор пользователей, компьютеров, учетных записей служб или групп** введите имя учетной записи агента моментальных снимков, созданной ранее, в виде <*имя_компьютера_издателя>***\repl_snapshot**. Выберите **Проверить имена** и нажмите кнопку **ОК**:  

    ![Добавление разрешений на общий доступ](media/tutorial-preparing-the-server-for-replication/addshareperms.png)

7. Повторите шаг 6 и добавьте две другие ранее созданные учетные записи: <*имя_компьютера_издателя>***\repl_merge** и <*имя_компьютера_издателя>***\repl_distribution**

8. После добавления этих трех учетных записей назначьте следующие разрешения:      
    - repl_distribution — «Чтение»;  
    - repl_merge — «Чтение».  
    - repl_snapshot — «Полный контроль»;    

  ![Разрешения на общий доступ](media/tutorial-preparing-the-server-for-replication/sharedpermissions.png)

9. После настройки разрешений на общий доступ нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Разрешения для ресурса repldata**. Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Расширенная настройка общего доступа**. 

10.  В диалоговом окне **Свойства repldata** перейдите на вкладку **Безопасность** и выберите **Изменить**:  

       ![Изменение параметров безопасности](media/tutorial-preparing-the-server-for-replication/editsecurity.png)   

11. В диалоговом окне **Разрешения для ресурса repldata** выберите **Добавить**. В текстовом поле **Выбор пользователей, компьютеров, учетных записей служб или групп** введите имя учетной записи агента моментальных снимков, созданной ранее, в виде <*имя_компьютера_издателя>***\repl_snapshot**. Выберите **Проверить имена** и нажмите кнопку **ОК**:  

    ![Добавление разрешений безопасности](media/tutorial-preparing-the-server-for-replication/addsecuritypermissions.png)

  
12.  Повторите предыдущий шаг, чтобы добавить разрешения для агента распространителя в формате <*имя_компьютера_издателя>***\repl_distribution** и для агента слияния в формате <* имя_компьютера_издателя>***\repl_merge**.  
    
  
13. Убедитесь в том, что следующие разрешения допустимы:  
  
    - repl_distribution — «Чтение»;
    - repl_merge — «Чтение».
    - repl_snapshot — «Полный контроль»;   
 
    ![Разрешения пользователя на данные репликации](media/tutorial-preparing-the-server-for-replication/replpermissions.png) 

14. Снова откройте вкладку **Общий доступ** и запишите значение **Сетевой путь** для общей папки. Этот путь вам понадобится позднее при настройке **папки моментальных снимков**:  

    ![Сетевой путь](media/tutorial-replicating-data-between-continuously-connected-servers/networkpath.png)

15. Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Свойства repldata**. 
 
**См. также**:  
[Организация безопасности папки моментальных снимков](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  

## <a name="configure-distribution"></a>Настройка распространителя
В этом разделе вам предстоит настроить распространение на издателе и установить необходимые разрешения для баз данных публикации и распространителя. Если распространитель уже настроен, необходимо отключить публикацию и распространение перед тем, как начать работу с этим разделом. Не следует этого выполнять в случае, если необходимо сохранить существующую топологию репликации, особенно в рабочей среде.   
  
Настройка издателя с удаленным распространителем не рассматривается в этом учебнике.  

### <a name="configure-distribution-at-the-publisher"></a>Настройка распространителя на издателе  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Щелкните правой кнопкой мыши папку **Репликация** и выберите пункт **Настройка распространения**:  

    ![Настройка распространителя](media/tutorial-preparing-the-server-for-replication/configuredistribution.png)
  
    > [!NOTE]  
    > Если подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлено с помощью **localhost** , а не фактического имени сервера, на экране появится предупреждение о том, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может подключиться к серверу **'localhost'**. В диалоговом окне предупреждения нажмите кнопку **ОК**. В диалоговом окне **Соединение с сервером** измените значение в поле **Имя сервера** с **localhost** на имя своего сервера. Выберите **Подключиться**.  
  
    Будет запущен мастер настройки распространителя.  
  
3.  На странице **Распространитель** выберите  **"имя_сервера", который будет выступать в качестве своего собственного распространителя; SQL Server создаст базу данных распространителя и журнал**, а затем нажмите кнопку **Далее**:  

    ![Этот сервер является своим собственным распространителем](media/tutorial-preparing-the-server-for-replication/serverdistributor.png)
  
4.  Если агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не запущен, на странице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Запуск агента** выберите **Да** и настройте автоматический запуск службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Выберите **Далее**.  

     
5.  Введите путь \\\\<*имя_компьютера_издателя>***\repldata** в текстовое поле **Папка моментальных снимков**, после чего нажмите кнопку **Далее**. Этот путь должен соответствовать значению **Сетевой путь** для папки свойств repldata, которое вы записали ранее после настройки свойств общей папки: 

    ![Папка моментальных снимков данных репликации](media/tutorial-preparing-the-server-for-replication/repldatasnapshot.png)
  
6.  Примите значения по умолчанию на оставшихся страницах мастера:  
    
    ![Значение по умолчанию в мастере настройки распространения](media/tutorial-preparing-the-server-for-replication/distributionwizarddefaults.png)
  
7.  Чтобы включить распространение, нажмите кнопку **Готово**. 

    Эта ошибка может отображаться при настройке распространителя. Она указывает на то, что учетная запись, которая использовалась для запуска учетной записи агента SQL Server, не является администратором системы. В этом случае вам необходимо вручную запустить агент SQL Server, предоставить соответствующие разрешения существующей учетной записи либо использовать другую учетную запись для агента SQL Server: 

     ![Ошибка при запуске агента](media/tutorial-preparing-the-server-for-replication/startingagenterror.png)

    Если среда SQL Server Management Studio запущена с правами администратора, вы можете вручную запустить агент SQL из нее:  
        ![Запуск агента из среды SSMS](media/tutorial-preparing-the-server-for-replication/ssmsstartagent.png) 

    >[!NOTE]
    > Если признаков запуска агента SQL не наблюдается, щелкните правой кнопкой мыши агент SQL Server в среде SSMS и выберите пункт **Обновить**.  Если агент по-прежнему остановлен, вам необходимо запустить его вручную с помощью **диспетчера конфигурации SQL Server**.    
  
### <a name="setting-database-permissions-at-the-publisher"></a>Установка разрешений базы данных на издателе  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] разверните узел **Безопасность**, щелкните правой кнопкой мыши **Имена входа**, а затем выберите пункт **Создать имя входа**:  

    ![Создать имя входа](media/tutorial-preparing-the-server-for-replication/newlogin.png)
  
2.  На странице **Общие** выберите **Найти**, введите <*компьютера_издателя>***\repl_snapshot** в поле **Введите имя объекта**, выберите **Проверить имена** и нажмите кнопку **ОК**:  

    ![Добавление имени для входа для моментального снимка репликации](media/tutorial-preparing-the-server-for-replication/addsnapshotlogin.png)
  
3.  На странице **Сопоставление пользователя** в списке **Пользователи, сопоставленные с этим именем входа** выберите **distribution** и базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
    В списке "Членство в роли базы данных" выберите роль **db_owner** для этого имени входа в обеих базах данных:  

    ![Владелец базы данных моментальных снимков репликации](media/tutorial-preparing-the-server-for-replication/dbowner.png)
  
4.  Нажмите кнопку **ОК**, чтобы создать имя входа.  
  
5.  Повторите шаги с 1 по 4, чтобы создать имена входа для других локальных учетных записей (repl_distribution, repl_logreader и repl_merge). Эти имена входа должны быть сопоставлены с пользователями, которые являются членами предопределенной роли базы данных **db_owner** в базах данных **распространителя** и **AdventureWorks**:  

    ![Пользователи репликации в среде SSMS](media/tutorial-preparing-the-server-for-replication/usersinssms.png)
  
  
**См. также**:  
[Настройка распространения](../../relational-databases/replication/configure-distribution.md)  
[Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md)  

## <a name="next-steps"></a>Следующие шаги
Вы успешно подготовили сервер для репликации. В следующей статье вы ознакомитесь с настройкой репликации транзакций. 

Перейдите к следующей статье, чтобы узнать больше
> [!div class="nextstepaction"]
> [Следующие шаги](tutorial-replicating-data-between-continuously-connected-servers.md)

  
  
