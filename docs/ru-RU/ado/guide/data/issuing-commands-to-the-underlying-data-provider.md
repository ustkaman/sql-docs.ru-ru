---
title: Выдача команды для базового поставщика данных | Документы Microsoft
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
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f217bd606dbc61db26430840c3b8dcdb79274d9d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Выдача команды для базового поставщика данных
Любые команды, не начинается с ФОРМОЙ передается поставщику данных. Это эквивалентно выполнению инструкции команды фигуры в форме «Формы {команды поставщика}». Эти команды имеют *не* нужно создать **записей**. Для экземпляра «{DROP ТАБЛИЦЕ MyTable} имеет ФОРМУ команде правильный фигуры, при условии, что поставщик данных поддерживает DROP TABLE.  
  
 Эта возможность позволяет команд обычного поставщика и команд формы для совместного использования одного соединения и транзакции.  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формальных фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
