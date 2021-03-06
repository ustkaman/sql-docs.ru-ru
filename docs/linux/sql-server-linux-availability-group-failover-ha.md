---
title: Управление отработки отказа группы доступности — SQL Server для Linux | Документы Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/01/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.openlocfilehash: 3a972495231c53506d440a3cc56bf4280cbeea0c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="always-on-availability-group-failover-on-linux"></a>Отработка отказа группы доступности AlwaysOn в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В контексте группы доступности (AG) роли первичной и вторичной реплик доступности обычно являются взаимозаменяемыми в процессе, называемом отработки отказа. Существуют три формы перехода на другой ресурс: автоматический переход на другой ресурс (без потери данных), запланированный переход на другой ресурс вручную (без потери данных) и принудительный переход на другой ресурс вручную (с возможной потерей данных), обычно именуемый *принудительным переходом на другой ресурс*. Все данные сохраняются при автоматическом и запланированном другой ресурс вручную. Группы Доступности при сбое на уровне реплики доступности. То есть группе Доступности переходит на одну из ее вторичных реплик (текущей цели отработки отказа). 

Дополнительные сведения об отработке отказа см. в разделе [отработка отказа и режимы](../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md).

## <a name="failover"></a>Отработка отказа вручную

Используйте средства управления кластером для отработки отказа группы Доступности, управляемых диспетчером внешних кластера. Например, если решение использует Pacemaker для управления кластером Linux, используйте `pcs` для выполнения ручной переход на другой ресурс RHEL или Ubuntu. На SLES используйте `crm`. 

> [!IMPORTANT]
> В обычных условиях при сбое с помощью Transact-SQL или SQL Server средства управления, такие как среда SSMS или PowerShell. Когда `CLUSTER_TYPE = EXTERNAL`, единственное допустимое значение для `FAILOVER_MODE` — `EXTERNAL`. Эти параметры все действия ручной или автоматический переход на другой ресурс, выполняются диспетчером внешних кластеров. Инструкции Принудительное переключение с возможной потерей данных см. в разделе [Принудительное переключение](#forceFailover).

### <a name="a-namemanualfailovermanual-failover-steps"></a><a name="manualFailover">Действия перехода на другой ресурс вручную

Переход на другой ресурс, вторичная реплика, которая станет первичной реплики должны быть синхронными. Если вторичная реплика является асинхронным, [изменение режима доступности](../database-engine/availability-groups/windows/change-the-availability-mode-of-an-availability-replica-sql-server.md).

Вручную при сбое в два этапа.

   Во-первых,[ вручную перевести на перемещение ресурсов группы Доступности](#manualMove) с узла кластера, которому принадлежит ресурсы на новый узел.

   Кластер при сбое ресурса группы Доступности и добавляет ограничение расположения. Это ограничение настраивает ресурсов для запуска на новый узел. Удалите это ограничение, чтобы успешно выполнять отработку отказа в будущем.

   Во-вторых, [удалить ограничение расположения](#removeLocConstraint).

#### <a name="a-namemanualmovestep-1-manually-fail-over-by-moving-availability-group-resource"></a><a name="manualMove">Шаг 1. Переход на другой вручную на перемещение ресурса группы доступности

Чтобы вручную перевести ресурс группы Доступности с именем *ag_cluster* на узел кластера с именем *nodeName2*, выполните соответствующую команду для распространения:

- **Пример RHEL/Ubuntu**

   ```bash
   sudo pcs resource move ag_cluster-master nodeName2 --master
   ```

- **Пример SLES**

   ```bash
   crm resource migrate ag_cluster nodeName2
   ```

>[!IMPORTANT]
>После вручную переключить ресурс, необходимо удалить ограничение расположения, которое автоматически добавляется.

#### <a name="a-nameremovelocconstraint-step-2-remove-the-location-constraint"></a><a name="removeLocConstraint"> Шаг 2. Удаление ограничения расположения

При отработке отказа вручную `pcs` команда `move` или `crm` команда `migrate` добавляет ограничение расположения для ресурса на новый целевой узел. Чтобы увидеть новое ограничение, после перемещения ресурса вручную выполните следующую команду:

- **Пример RHEL/Ubuntu**

   ```bash
   sudo pcs constraint --full
   ```

- **Пример SLES**

   ```bash
   crm config show
   ```

Удалите ограничение расположение, будущих переход на другой ресурс — включая автоматический переход на другой ресурс — успешно. 

Чтобы удалить ограничение, выполните следующую команду: 

- **Пример RHEL/Ubuntu**

   В этом примере `ag_cluster-master` имя ресурса, который отработку отказа. 

   ```bash
   sudo pcs resource clear ag_cluster-master 
   ```

- **Пример SLES**

   В этом примере `ag_cluster` имя ресурса, который отработку отказа. 

   ```bash
   crm resource clear ag_cluster
   ```

Вы также можете выполнить приведенную ниже команду для удаления ограничения расположения,  

- **Пример RHEL/Ubuntu**

   где `cli-prefer-ag_cluster-master` — это код ограничения, которое необходимо удалить. `sudo pcs constraint --full` возвращает этот код. 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```
- **Пример SLES**

   В следующей команде `cli-prefer-ms-ag_cluster` идентификатор ограничения. `crm config show` возвращает этот код. 
   
   ```bash
   crm configure
   delete cli-prefer-ms-ag_cluster 
   commit
   ```

>[!NOTE]
>При автоматическом переходе на другой ресурс ограничение расположения не добавляется, поэтому очистка не требуется. 

Дополнительные сведения см. в следующих разделах:
- [Chapter 7. Managing Cluster Resources](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-manageresource-HAAR.html) (Глава 7. Управление ресурсами кластера)
- [Pacemaker - вручную переместить ресурсы](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-pcs/html/Clusters_from_Scratch/_move_resources_manually.html)
 [руководство по администрированию SLES - ресурсы](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.resource) 
 
## <a name="forceFailover"></a> Принудительная отработка отказа 

Принудительная отработка отказа, предназначенная исключительно для аварийного восстановления. В этом случае нельзя переключением с помощью средства управления кластером, так как основной ЦОД не работает. Если выполняется принудительный переход на несинхронизированную вторичную реплику, возможна потеря данных. Принудительный переход только в том случае, если требуется немедленное восстановление доступа к группе Доступности и допускается риск потери данных.

Если нельзя использовать средства управления кластером для взаимодействия с кластером — например, если кластер не отвечает из-за аварии в центре обработки данных источника, может потребоваться выполнить принудительный переход для обхода Диспетчер внешних кластера. Эту процедуру для выполнения обычных операций не рекомендуется, поскольку существует риск потери данных. Применяется, если не удастся выполнить действие по отработке отказа средства управления кластером. Функционально, эта процедура аналогична [Принудительная отработка отказа вручную](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) в группе Доступности в Windows.
 
Этот процесс для принудительной отработки отказа для сервера SQL Server в Linux.

1. Убедитесь, что ресурс группы Доступности не находится под управлением кластера больше. 

      - Установка ресурса в неуправляемой режим на целевом узле кластера. Эта команда сообщает агенту ресурсов для управления и мониторинга ресурсов stop. Например: 
      
      ```bash
      sudo pcs resource unmanage <resourceName>
      ```

      - При неудачной попытке задания режима ресурсов в неуправляемых режим, удалите данный ресурс. Например:

      ```bash
      sudo pcs resource delete <resourceName>
      ```

      >[!NOTE]
      >При удалении ресурса также удаляет все связанные ограничения. 

1. На экземпляре SQL Server, на котором размещена вторичная реплика, присвойте переменной контекста сеанса `external_cluster`.

   ```Transact-SQL
   EXEC sp_set_session_context @key = N'external_cluster', @value = N'yes';
   ```

1. Переход группы Доступности, с помощью Transact-SQL. В следующем примере замените `<MyAg>` на имя вашей группы Доступности. Подключитесь к экземпляру SQL Server, на котором размещена целевая вторичная реплика и выполните следующую команду:

   ```Transact-SQL
   ALTER AVAILABILITY GROUP <MyAg> FORCE_FAILOVER_ALLOW_DATA_LOSS;
   ```

1.  После принудительной отработки отказа переведите AG в работоспособное состояние до перезапуска мониторинг ресурсов кластера и управления или повторного создания ресурса группы Доступности. Просмотрите [основные задачи после принудительной отработки отказа](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md#FollowUp).

1.  Либо перезапустите мониторинг ресурсов кластера и управления:

   Чтобы перезапустить мониторинг ресурсов кластера и управления, выполните следующую команду:

   ```bash
   sudo pcs resource manage <resourceName>
   sudo pcs resource cleanup <resourceName>
   ```

   Если вы удалили ресурса кластера, создайте ее. Чтобы повторно создать ресурс кластера, следуйте инструкциям в [Создание группы доступности](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource).

>[!Important]
>Не используйте описанные выше шаги для аварийного восстановления, так как существует риск потери данных. Вместо этого измените асинхронная реплика для синхронных и инструкции по [обычный отработка отказа вручную](#manualFailover).

## <a name="database-level-monitoring-and-failover-trigger"></a>Уровень мониторинга и переход на другой ресурс для триггера базы данных

Для `CLUSTER_TYPE=EXTERNAL`, семантика триггер отработки отказа различаются по сравнению с WSFC. Если группе Доступности на экземпляре SQL Server в WSFC, переход из `ONLINE` состояние для базы данных вызывает работоспособности группы Доступности для сообщения ошибки. В ответ диспетчер кластеров инициирует действие отработки отказа. В Linux экземпляр SQL Server не удается связаться с кластером. Мониторинг работоспособности базы данных выполняется *за пределами в*. Если пользователь выбрал в для мониторинга отработки отказа базы данных и обеспечения отказоустойчивости (путем установки параметра `DB_FAILOVER=ON` при создании группы Доступности), кластер будет проверять, если состояние базы данных является `ONLINE` при каждом запуске действие мониторинга. Кластер запрашивает состояние в `sys.databases`. Для любого состояния, отличный от `ONLINE`, инициирует отработку отказа автоматически (если выполнены условия для автоматического перехода на другой ресурс). Фактическое время отработки отказа зависит от частоты действие мониторинга, а также состояние базы данных обновляются в представлении каталога sys.databases.

Автоматический переход на другой ресурс требуется по крайней мере одна реплика.

## <a name="next-steps"></a>Следующие шаги

[Настройка Red Hat Enterprise Linux кластера для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Настройка SUSE Linux Enterprise Server кластера для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Настройка кластера Ubuntu для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
