---
title: Метод (SQLServerResultSet) deleteRow | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.deleteRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd06dec2dccd3e124d702131aa4520a394ecd9fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="deleterow-method-sqlserverresultset"></a>deleteRow метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Удаляет текущую строку из этого[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта и из базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void deleteRow()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод deleteRow указывается с помощью метода deleteRow в интерфейсе java.sql.ResultSet.  
  
 Этот метод не может быть вызван при нахождении курсора в строке вставки.  
  
 Если используются курсоры, управляемые набором ключей, этот метод оставляет пробел в результирующем наборе. Можно проверить с помощью этого отверстия в центре [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md) метод. Номера строк в результирующем наборе не изменяются.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
