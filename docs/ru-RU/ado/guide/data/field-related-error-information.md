---
title: Сведения об ошибке, относящееся к полю | Документы Microsoft
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
helpviewer_keywords:
- field-related errors [ADO]
- errors [ADO], field-related
ms.assetid: 5e7b1af4-996b-47c5-9161-c5575ad4fec9
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7491e713f68ee44cd48bf9c53db013a4424e1d1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="field-related-error-information"></a>Сведения об ошибке, относящееся к полю
Если ошибка непосредственно связаны с полем — например, отсутствие данных, или если он имеет неверный тип для поля, можно получить дополнительные сведения о причине проблемы с помощью проверки **поле** объекта **состояния**  свойство. Это свойство была расширена для предоставления определенных сведений о проблеме. Так, например, при вызове **UpdateBatch** завершается ошибкой, причиной проблемы может определить, проверив **состояние** свойство **поля** в каждом из данных записи. Это свойство будет содержать одно из значений в **FieldStatusEnum** константой. В следующей таблице представлены те значения, которые представляют интерес при возникновении ошибки.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adFieldCantConvertValue**|2|Указывает на поле извлечь или хранятся без потери данных.|  
|**adFieldDataOverflow**|6|Указывает, что, возвращенный поставщиком данных переполняет тип данных поля.|  
|**adFieldDefault**|13|Указывает, что значение по умолчанию для поля использовался при вводе данных.|  
|**adFieldIgnore**|15|Указывает, что это поле был пропущен при значения параметра данных в источнике. Значение не задано поставщиком.|  
|**adFieldIntegrityViolation**|10|Указывает, что поле не может изменяться, так как это вычисленное или производное сущности.|  
|**adFieldIsNull**|3|Указывает, что поставщик возвратил значение null.|  
|**adFieldOutOfSpace**|22|Указывает, что поставщик не удается получить достаточно места для завершения перемещения или копирования операции.|
