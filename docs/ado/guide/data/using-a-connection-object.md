---
title: С помощью объекта соединения | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 4b34f971-5699-43e7-9b15-137d334fa66e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 24dd06d812a1234fd9a7458600e71f77cccdcf63
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-a-connection-object"></a>С помощью объекта соединения
Прежде чем открывать **подключения** объекта, необходимо определить определенные сведения об источнике данных и тип соединения. Большая часть этих сведений, удерживается *ConnectionString* параметр [метод Open](../../../ado/reference/ado-api/open-method-ado-connection.md) на **подключения** объекта, или с помощью [ConnectionString Свойство](../../../ado/reference/ado-api/connectionstring-property-ado.md) на **подключения** объекта. Строка подключения состоит из списка пар аргументов и значений, значения, заключенные в одинарные кавычки, разделенные точкой с запятой. Например:  
  
```  
Dim sConn As String  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
```  
  
> [!NOTE]
>  Можно также указать имя источника ODBC данных (DSN) или файл Data Link (UDL) в строке подключения. Дополнительные сведения о источников данных см. в разделе [Управление источниками данных](../../../odbc/admin/managing-data-sources.md) в справочнике программиста ODBC. Дополнительные сведения о UDL см. в разделе [Обзор API связи данных](http://msdn.microsoft.com/en-us/95c180ea-bd4f-4dca-b95a-576afd135bbc) в справочнике программиста OLE DB.  
  
 Как правило, установить соединение путем вызова **Connection.Open** метод с соответствующим *строка подключения* параметром. Пример показан в следующем фрагменте кода Visual Basic:  
  
```  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
' Open a connection.  
Set oConn = New ADODB.Connection  
.Open   
  
' Make a query over the connection.  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, , adOpenStatic, adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
' Close the connection.  
oConn.Close  
Set oConn = Nothing  
  
```  
  
 Здесь **oRs.Open** принимает **подключения** объекта (*oConn*) в качестве значения переменной его *ActiveConnection* параметра. Кроме того **Connection.CursorLocation** свойство принимает значение по умолчанию **adUseServer**. Этот параметр, чтобы сравнить [HelloData](../../../ado/guide/data/hellodata-a-simple-ado-application.md) примере в предыдущем разделе. Следующая инструкция приведет к ошибке во время выполнения.  
  
```  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
```
