---
title: Пример свойства CacheSize (VB) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- CacheSize property [ADO], Visual Basic example
ms.assetid: a237ffdb-6e5b-47c6-9901-d5cdbe8625f3
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db1ca788bbaa120d2eff5f8b13818de7936e2761
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="cachesize-property-example-vb"></a>Пример свойства CacheSize (Visual Basic)
В этом примере используется [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) свойство, которое отображает разницу в производительности для операции, выполняемая с и без 30 записи кэша.  
  
```  
'BeginCacheSizeVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim rstRoySched As ADODB.Recordset  
    Dim strSQLSched As String  
    Dim strCnxn As String  
     'record variables  
    Dim sngStart As Single  
    Dim sngEnd As Single  
    Dim sngNoCache As Single  
    Dim sngCache As Single  
    Dim intLoop As Integer  
    Dim strTemp As String  
  
    ' Open the connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
  
    ' Open the RoySched Table  
    Set rstRoySched = New ADODB.Recordset  
    strSQLSched = "roysched"  
    rstRoySched.Open strSQLSched, strCnxn, , , adCmdTable  
  
    ' Enumerate the Recordset object twice and  
    ' record the elapsed time  
    sngStart = Timer  
  
    For intLoop = 1 To 2  
        rstRoySched.MoveFirst  
  
        If Not rstRoySched.EOF Then  
            ' Execute a simple operation for the  
            ' performance test  
            Do  
                strTemp = rstRoySched!title_id  
                rstRoySched.MoveNext  
            Loop Until rstRoySched.EOF  
        End If  
    Next intLoop  
  
    sngEnd = Timer  
    sngNoCache = sngEnd - sngStart  
  
    ' Cache records in groups of 30 records.  
    rstRoySched.MoveFirst  
    rstRoySched.CacheSize = 30  
    sngStart = Timer  
  
    ' Enumerate the Recordset object twice and record  
    ' the elapsed time  
    For intLoop = 1 To 2  
        rstRoySched.MoveFirst  
        Do While Not rstRoySched.EOF  
            ' Execute a simple operation for the  
            ' performance test  
            strTemp = rstRoySched!title_id  
            rstRoySched.MoveNext  
        Loop  
    Next intLoop  
  
    sngEnd = Timer  
    sngCache = sngEnd - sngStart  
  
    ' Display performance results.  
    MsgBox "Caching Performance Results:" & vbCr & _  
        "   No cache: " & Format(sngNoCache, "##0.000") & " seconds" & vbCr & _  
        "   30-record cache: " & Format(sngCache, "##0.000") & " seconds"  
  
    ' clean up  
    rstRoySched.Close  
    Set rstRoySched = Nothing  
    Exit Sub  
  
ErrorHandler:  
   ' clean up  
    If Not rstRoySched Is Nothing Then  
        If rstRoySched.State = adStateOpen Then rstRoySched.Close  
    End If  
    Set rstRoySched = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndCacheSizeVB  
```  
  
## <a name="see-also"></a>См. также  
 [Свойство CacheSize (ADO)](../../../ado/reference/ado-api/cachesize-property-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
