---
title: Использование метаданных базы данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2f3e0a4e19b30eeb494f89281a01195cf98b7d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-database-metadata"></a>Использование метаданных базы данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Для запросов к базе данных сведения о его поддержке [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализует [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) класса. Этот класс содержит многочисленные методы, которые возвращают сведения в виде одного значения или результирующего набора.  
  
 Чтобы создать объект SQLServerDatabaseMetaData, можно использовать [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) для получения сведений о базе данных, что она подключена к.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, метод getMetaData класса SQLServerConnection используется для возврата объекта SQLServerDatabaseMetadata, а затем различные методы объекта Объект SQLServerDatabaseMetaData используются для отображения сведений о драйвера, версии драйвера, имени базы данных и версии базы данных.  
  
 [!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]  
  
## <a name="see-also"></a>См. также  
 [Обработка метаданных с использованием драйвера JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  
