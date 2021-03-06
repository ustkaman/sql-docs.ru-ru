---
title: Диалоговое окно "Выполнение политик", страница "Выбор политики" | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.dmf.runnow.f1
ms.assetid: 20075fbe-0b48-42c8-b747-690f1aa23dcf
caps.latest.revision: 36
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a92afcb9fec91f099b9ffbee048d5d2f2df884e2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="evaluate-policies-dialog-box-policy-selection-page"></a>Диалоговое окно «Выполнение политик», страница «Выбор политики»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Используйте это диалоговое окно для оценки политик управления на основе политик. При выборе страницы **Результаты оценки** можно применить политики к элементам в наборе целей, которые не соответствуют политикам.  
  
## <a name="options"></a>Параметры  
 **Source**  
 Задает источник политик. Чтобы изменить источник, нажмите кнопку обзора (**...**), чтобы открыть диалоговое окно **Выбор источника** .  
  
 **Файлы**  
 Введите путь к файлу, содержащему политику управления на основе политик, или нажмите кнопку обзора (**...**), чтобы выбрать файл.  
  
 **Server**  
 Выберите, чтобы подключиться к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , содержащего нужную политику.  
  
 **Политики: политика**  
 Нажмите, чтобы открыть диалоговое окно для указанной политики.  
  
 **Политики: категория**  
 Категория политики. Поле доступно только для чтения.  
  
 **Политики: аспект**  
 Аспект, реализуемый политикой. Поле доступно только для чтения.  
  
 **Вычислить**  
 Запускает политику в режиме оценки. Создает отчет о соответствии политике для набора целей, но не изменяет конфигурацию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не обеспечивает соблюдение политики в дальнейшем.  
  
## <a name="possible-errors"></a>Возможные ошибки  
  
-   **Цели не найдены**  
  
     Набор целей может быть пустым по любой из следующих причин.  
  
    -   В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нет целей с типом, указанным в политике.  
  
    -   Ограничение сервера может исключить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , содержащий цель.  
  
    -   Если политика задана для объекта в базе данных (таблицы, представления или пользователя), возможно, база данных не может подписаться на категорию политики.  
  
    -   Фильтр целевого набора может исключить все цели в данном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Тип целевого сервера отличается от типа сервера, на котором оценивается политика. Например, в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)]при попытке оценки политики, созданной для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], будет получен пустой набор целей.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Диалоговое окно «Выполнение политик», страница «Результаты выполнения»](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-evaluation-results-page.md)  
  
  
