---
title: Состояние синхронизации данных базы данных доступности не в рабочем состоянии | Документы Майкрософт
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
- sql13.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: erikre
ms.openlocfilehash: fec52227f571a804f914c9d2278276519ebab35e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a>Состояние синхронизации данных баз данных доступности не является исправным
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние синхронизации базы данных доступности|  
|**Проблема**|Состояние синхронизации данных некоторых баз данных доступности не является рабочим.|  
|**Категория**|**Предупреждение**|  
|**Аспект**|База данных доступности|  
  
## <a name="description"></a>Description  
 Эта политика выполняет сведение состояния синхронизации данных для всех баз данных доступности (которые также называются «реплики баз данных») в реплике доступности. Политика находится в нерабочем состоянии при нахождении какой-либо из реплик баз данных в непредвиденном состоянии синхронизации данных. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях доступны в разделе [Состояние синхронизации данных некоторых баз данных доступности не является исправным](http://go.microsoft.com/fwlink/p/?LinkId=220858) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Состояние синхронизации данных некоторых баз данных доступности не является рабочим. Если это реплика доступности с асинхронной фиксацией, все базы данных доступности должны находиться в состоянии SYNCHRONIZING. При синхронной фиксации реплик доступности у всех баз данных доступности должно быть состояние SYNCHRONIZED.  
  
## <a name="possible-solution"></a>Возможное решение  
 Используйте политику реплик баз данных для поиска реплики баз данных с нерабочим состоянием синхронизации данных и устраните проблему в реплике базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](~/database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  


