---
title: Позиционирование записей | Документы Microsoft
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
- record positioning [ADO]
- Recordset object [ADO]
- repositioning record [ADO]
- AbsolutePosition property [ADO]
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0bb579a63f25207d44f5211afca78831d5cabaad
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="recordset-positioning"></a>Позиционирование записей
Используйте **AbsolutePosition** на основе свойства, чтобы перейти к записи по его порядковому номеру в **записей** объекта, или чтобы определить порядковый номер текущей записи. Поставщик должен поддерживать соответствующие функциональные возможности для этого свойства доступно.  
  
 **AbsolutePosition** начинается с 1 и имеет значение 1, если текущая запись является первой записью в **записей**. Как упоминалось ранее, вы можете получить общее число записей в **записей** объекта из **RecordCount** свойство.  
  
 При задании **AbsolutePosition** свойство, даже если это записи в текущий кэш ADO перезагружает кэша с новой группой записей, начиная с указанной записи. **CacheSize** свойство определяет размер этой группы.  
  
> [!NOTE]
>  Не следует использовать **AbsolutePosition** свойство в качестве символов-заместителей номер записи. Позиция изменения определенной записи, при удалении предыдущей записи. Нет никакой гарантии, что данная запись будет иметь такой же также **AbsolutePosition** Если **записей** опросить или повторном открытии объекта. Закладки являются рекомендуемый способ сохранения и возврат к заданной позиции, а единственный способ размещения различных типов **записей** объектов.
