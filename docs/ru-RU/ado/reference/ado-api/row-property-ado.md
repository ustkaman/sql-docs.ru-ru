---
title: Строка свойства (ADO) | Документы Microsoft
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
apitype: COM
f1_keywords:
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords:
- Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65ef451a62023eea3139098370bd3b65f6352811
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="row-property-ado"></a>Свойства строки (ADO)
Возвращает или задает поставщика OLE DB **строки** объект из или в [ADORecordConstruction интерфейс](../../../ado/reference/ado-api/adorecordconstruction-interface.md) объекта. При использовании **put_Row** для задания **строки** объекта строки преобразуются в ADO **записи** объекта.  
  
## <a name="readwritesyntax"></a>Чтение и запись. Синтаксис  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>Параметры  
 *ppRow*  
 Указатель на OLE DB **строки** объекта.  
  
 *PRow*  
 OLE DB **строки** объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Этот метод свойство возвращает стандартные значения HRESULT, включая S_OK и E_FAIL.  
  
## <a name="applies-to"></a>Объект применения  
 [Интерфейс ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
