---
title: Свойства подписчика | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
caps.latest.revision: 22
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5321e8a5770a9b15a50a5a80b998fa0f8ac4bdaa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="subscriber-properties"></a>Свойства подписчика
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Свойства подписчика** содержит сведения, относящиеся к подписчикам, использующим версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , предшествующие [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="options"></a>Параметры  
 **Соединение агента с подписчиком**  
 Контекст, в котором агент распространителя и агент слияния устанавливают соединение от распространителя к подписчику. Применяется только к версиям, предшествующим [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Выберите **Выполнять олицетворение учетной записи процесса агента** для соединения с подписчиком при помощи контекста учетной записи агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на распространителе или укажите **Проверка подлинности SQL Server**, а затем введите значения в поля **Имя входа** и **Пароль**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выбрать пункт **Выполнять олицетворение учетной записи процесса агента**.  
  
 Для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий данные о соединении указываются для каждой подписки в мастере создания подписки, их можно изменить в диалоговом окне **Свойства подписки** .  
  
 **Расписания агентов по умолчанию**  
 Расписание по умолчанию, используемое в мастере создания подписки для подписчиков, использующих версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , предшествующие [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 **Разное**  
 Содержит сведения о подписчике и типе подписчика.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Справочник по свойствам (репликация)](../../relational-databases/replication/properties-reference-replication.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
