---
title: "Состояние работоспособности монитора устройства (система платформы аналитики)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91132e3c-3137-4670-adaa-8a7b234fb8d2
caps.latest.revision: "12"
ms.openlocfilehash: dad3355061bafcbbfa3a34b21d2043b0411129ba
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="monitor-appliance-health-state"></a>Монитор состояния работоспособности устройства
В этом разделе объясняется, как осуществлять мониторинг состояния SQL Server PDW устройства с помощью консоли администрирования, или путем непосредственного запроса SQL Server PDW динамические административные представления.  
  
## <a name="to-monitor-the-appliance-state"></a>Чтобы отслеживать состояние устройства  
Системный администратор может использовать консоли администрирования или SQL Server PDW динамические административные представления (DMV), для получения полную иерархию узлов, компоненты и программного обеспечения. Следующая диаграмма представляет общее понимание компонентов, которые отслеживает SQL Server PDW.  
  
![Обзор монитора](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>Мониторинг состояния компонента с помощью консоли администрирования  
Чтобы получить состояние компонента с помощью консоли администрирования.  
  
1.  Щелкните **состояние устройства** вкладки.  
  
2.  На странице состояние устройства щелкните на определенном узле, чтобы просмотреть сведения об узле.  
  
    ![Состояние консоли администрирования PDW](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>Мониторинг состояния компонента с помощью системных представлений  
Получить состояние компонента с помощью системных представлений с помощью [sys.dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md). Например следующий запрос получает сведения о состоянии для всех компонентов.  
  
```sql  
SELECT   
   s.[pdw_node_id],  
   n.[name] as [node_name],  
   n.[address] ,  
   g.[group_id] ,  
   g.[group_name] ,  
   c.[component_id] ,  
   c.[component_name] ,  
   s.[component_instance_id] ,   
   p.[property_name] ,  
   s.[property_value] ,  
   s.[update_time]  
FROM [sys].[dm_pdw_component_health_status] AS s  
JOIN sys.dm_pdw_nodes AS n   
   ON s.[pdw_node_id] = n.[pdw_node_id]  
JOIN [sys].[pdw_health_components] AS c   
   ON s.[component_id] = c.[component_id]  
JOIN [sys].[pdw_health_component_groups] AS g   
   ON c.[group_id] = g.[group_id]  
JOIN [sys].[pdw_health_component_properties] AS p   
   ON s.[property_id] = p.[property_id] AND s.[component_id] = p.[component_id]  
WHERE p.property_name = 'Status'  
ORDER BY  
   s.[pdw_node_id],  
   g.[group_name] ,   
   s.[component_instance_id] ,  
   c.[component_name] ,   
   p.[property_name];  
```  
  
Ниже перечислены возможные возвращаемые значения для свойства Status  
  
-   ОК  
  
-   Некритическая  
  
-   Критическая  
  
-   Unknown  
  
-   Не поддерживается  
  
-   Недоступен  
  
-   Без возможности восстановления  
  
Чтобы увидеть все свойства для всех компонентов, удалите `WHERE  p.property_name = 'Status'` предложения.  
  
**[Update_time]** отображается время последнего опроса компонента агентами работоспособности SQL Server PDW.  
  
> [!CAUTION]  
> Убедитесь, что определить причину проблемы, если компонент не будет опрашиваться 5 минут или более; может быть оповещение, которое указывает на проблему с пульса программного обеспечения.  
  
## <a name="see-also"></a>См. также:  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Мониторинг устройства &#40; Система платформы аналитики &#41;](appliance-monitoring.md)  
  