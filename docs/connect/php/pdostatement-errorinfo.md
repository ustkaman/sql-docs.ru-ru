---
title: PDOStatement::errorInfo | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e45bebe8-ea4c-49b6-93db-cf1ae65f530c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46c2cda3b7b36d534e02a8a4d3a782e3abd94240
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="pdostatementerrorinfo"></a>PDOStatement::errorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает расширенные сведения об ошибке для последней операции с дескриптором инструкции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array PDOStatement::errorInfo();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
Массив сведений об ошибке для последней операции с дескриптором инструкции. Этот массив состоит из следующих полей:  
  
-   Код ошибки SQLSTATE.  
  
-   Код ошибки, относящийся к драйверу.  
  
-   Сообщение об ошибке, относящееся к драйверу.  
  
Если ошибка отсутствует или не задан SQLSTATE, поля, относящиеся к драйверу, будут иметь значение NULL.  
  
## <a name="remarks"></a>Замечания  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
В этом примере инструкция SQL содержит ошибку, о которой затем сообщается.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print_r ($stmt->errorInfo());  
?>  
```  
  
## <a name="see-also"></a>См. также  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
