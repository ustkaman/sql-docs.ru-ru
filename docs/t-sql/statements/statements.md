---
title: Инструкции | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d8d6f62a-e815-425c-a80e-a63fd34ec275
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3418f30e95cfab213496dc5b1fbbc3b8a1dd35f4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="transact-sql-statements"></a>Инструкции Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

В этом справочном разделе перечислены категории инструкций для использования с Transact-SQL (T-SQL). Полный список инструкций приводится слева.

## <a name="backup-and-restore"></a>Резервное копирование и восстановление
Инструкции резервного копирования и восстановления позволяют создавать резервные копии и восстанавливать данные из резервных копий.  Дополнительные сведения см. в разделе [Общие сведения о резервном копировании и восстановлении](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).

## <a name="data-definition-language"></a>Язык описания данных DDL
Инструкции языка описания данных DDL определяют структуры данных. Эти инструкции используются для создания, изменения и удаления структур данных в базе данных.
- ALTER
- Параметры сортировки
- CREATE
- DROP
- DISABLE TRIGGER
- ENABLE TRIGGER
- RENAME
- UPDATE STATISTICS

## <a name="data-manipulation-language"></a>Язык обработки данных DML
Язык обработки данных (DML) влияет на информацию, хранящуюся в базе данных. Эти инструкции используются для вставки, обновления и изменение строк в базе данных.

- BULK INSERT
- DELETE
- INSERT
- MERGE
- TRUNCATE TABLE

## <a name="permissions-statements"></a>Инструкции разрешений
Инструкции разрешений определяют пользователей и имена входа, которые имеют доступ к данным и могут выполнять операции. Дополнительные сведения о проверке подлинности и доступе см. в разделе [Центра безопасности](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="service-broker-statements"></a>Инструкции компонента Service Broker
Service Broker — это компонент, который обеспечивает собственную поддержку приложений обмена сообщениями и приложений с очередями. Дополнительные сведения см. в разделе [Service Broker](../../relational-databases/service-broker/event-notifications.md).

## <a name="session-settings"></a>Параметры сеанса
Инструкции SET определяют, как текущий сеанс управляет параметрами времени выполнения. Общие сведения см. в разделе [Инструкций SET](set-statements-transact-sql.md).
