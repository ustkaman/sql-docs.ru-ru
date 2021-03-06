---
title: Страница ввода паролей (мастер добавления реплики) | Документы Майкрософт
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.addreplicawizard.enterpasswords.f1
ms.assetid: e69207a0-c5c4-44e4-ae9a-4afbb67251d1
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 64162e72b220d9355b982665c1a444df5eac8811
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="enter-passwords-page-add-replica-wizard"></a>Страница ввода паролей (мастер добавления реплики)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе справки описываются параметры, приведенные на странице **Ввод паролей** . Эта тема относится к [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Если реплики, выбранные на странице **Выбор реплик** , содержат базы данных с главным ключом, откроется страница "Ввод паролей".  
  
## <a name="enter-passwords-options"></a>Параметры ввода паролей  
 В сетке **Пользовательские базы данных в этом экземпляре SQL Server** перечислены все локальные пользовательские базы данных. Существуют следующие столбцы.  
  
 **Название**  
 Отображает имя локальной пользовательской базы данных.  
  
 **Размер**  
 Отображает размер базы данных, если он доступен мастеру.  
  
 **Состояние**  
 Указывает режим **Требуется пароль** для базы данных с главным ключом. Введя пароли для главных ключей базы данных в столбце **Пароли** , нажмите кнопку **Обновить**. Если пароли введены правильно, в столбце **Состояние** будет указано **Пароль введен**.  
  
 Если база данных не содержит главный ключ, в столбце **Состояние** будет указано **Пароль не требуется**.  
  
 **Пароль**  
 Если в столбце **Состояние** указано **Требуется пароль**, введите пароль для главного ключа базы данных.  
  
 **Обновить**  
 Щелкните, чтобы обновить сетку. Мы рекомендуем сделать это после ввода необходимых паролей.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Использование мастера добавления реплики в группу доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>См. также:  
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
