---
title: PDOStatement::bindParam | Документы Microsoft
ms.custom: ''
ms.date: 04/11/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 082af7aa2e6bcac8c44af1660c4a797515938aef
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Привязывает параметр к именованному заполнителю или заполнителю с вопросительным знаком в инструкции SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDOStatement::bindParam($parameter, &$variable[, $data_type[, $length[, $driver_options]]]);  
```  
  
#### <a name="parameters"></a>Параметры  
$*параметр*: идентификатор параметра (смешанное). Для инструкции, использующей именованные заполнители, используйте имя параметра (: имя). Для подготовленной инструкции, использующей синтаксис с вопросительным знаком это единицы индекс параметра.  
  
&$*переменная*: имя (смешанное) переменной PHP, привязываемой к параметру инструкции SQL.  
  
$*data_type*: константа PDO::PARAM_ * необязательно (целое число). Значение по умолчанию — PDO::PARAM_STR.  
  
$*Длина*: длина типа данных необязательно (целое число). Можно задать PDO::SQLSRV_PARAM_OUT_DEFAULT_SIZE, чтобы указать размер по умолчанию при использовании PDO::PARAM_INT или PDO::PARAM_BOOL в $*data_type*.  
  
$*driver_options*: необязательные параметры драйвера (смешанное). Например, можно указать PDO::SQLSRV_ENCODING_UTF8 для привязки столбца к переменной в виде строки с кодировкой UTF-8.  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение TRUE в случае успеха, в противном случае — значение FALSE.  
  
## <a name="remarks"></a>Замечания  
При привязке к столбцам сервера, имеющим тип varbinary, binary или varbinary(max) пустых данных следует указать двоичную кодировку (PDO::SQLSRV_ENCODING_BINARY) с помощью $*driver_options*. Дополнительные сведения о константах кодирования см. в разделе [константы](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

## <a name="example"></a>Пример  
Этот пример кода показывает, что после привязки значения $contact к параметру изменение этого значения приводит к изменению значения, передаваемого в запрос.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="example"></a>Пример  
Этот пример кода показывает, как получить доступ к параметру вывода.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(*) from Sys.tables");  
$stmt->bindParam(1, $input1, PDO::PARAM_STR, 10);  
$stmt->execute();  
echo $input1;  
?>  
```  
  
> [!NOTE]
> При привязке выходной параметр типа bigint, если значение может оказаться за пределами диапазона [целое](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md), использование PDO::PARAM_INT с PDO::SQLSRV_PARAM_OUT_DEFAULT_SIZE может привести к исключению «значение вне допустимого диапазона». Таким образом вместо этого используйте значение по умолчанию PDO::PARAM_STR и укажите размер полученной строке, не более 21. Это максимальное число цифр, включая знак минус любого значения типа bigint. 

## <a name="example"></a>Пример  
Этот пример кода показывает, как получить доступ к параметру ввода/вывода.  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  

> [!NOTE]
> Рекомендуется использовать строки в качестве входных данных при привязке значения [столбца decimal или numeric](../../t-sql/data-types/decimal-and-numeric-transact-sql.md) для обеспечения точности и точность как PHP имеет ограниченную точность для [чисел с плавающей запятой](http://php.net/manual/en/language.types.float.php).

## <a name="example"></a>Пример  
В этом примере кода показано, как привязать десятичное значение в качестве входного параметра.  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```


## <a name="see-also"></a>См. также  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
