---
title: Поставщик Microsoft OLE DB для Oracle | Документы Microsoft
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
- providers [ADO], OLE DB provider for Oracle
- OLE DB provider for Oracle [ADO]
- Oracle provider [ADO]
ms.assetid: 44fae9dd-5585-4cd6-8bbd-3248a78931b4
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de312ff17a7d66bf58a5b8f1fb7a6c33aa27acec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="microsoft-ole-db-provider-for-oracle-overview"></a>Поставщик Microsoft OLE DB для Oracle Обзор
> [!IMPORTANT]
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте поставщик OLE DB для Oracle.

 Поставщик Microsoft OLE DB для Oracle позволяет ADO для доступа к базам данных Oracle.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этому поставщику, задайте *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```
MSDAORA
```

 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство возвратит также этой строки.

 Запрос соединения с набором ключей или динамического курсора при выполнении в базе данных Oracle, возникает ошибка. Oracle поддерживает только статический курсор только для чтения.

## <a name="typical-connection-string"></a>Обычная строка соединения
 — Строка соединения для данного поставщика:

```
"Provider=MSDAORA;Data Source=serverName;User ID=MyUserID; Password=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для Oracle.|
|**Источник данных**|Указывает имя сервера.|
|**Идентификатор пользователя**|Указывает имя пользователя.|
|**Пароль**|Указывает пароль пользователя.|

> [!NOTE]
>  При подключении к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

## <a name="provider-specific-connection-parameters"></a>Параметры подключения для конкретного поставщика
 Поставщик поддерживает несколько параметров подключения к конкретному поставщику помимо параметрами, определенными ADO. Как с помощью свойства соединения ADO, эти свойства от поставщика может быть задано посредством [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию [подключения](../../../ado/reference/ado-api/connection-object-ado.md) или как часть **ConnectionString**.

 Эти параметры являются полностью описаны в [Справочник программиста OLE DB](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8). [Индекс динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) предоставляет перекрестной ссылки между эти имена параметров и соответствующие свойства OLE DB.

|Параметр|Описание|
|---------------|-----------------|
|**Дескриптор окна**|Указывает дескриптор окна для использования для запроса дополнительных сведений.|
|**Идентификатор локали**|Указывает уникальный 32-разрядное число (например, 1033), указывающее параметры, связанные с языком пользователя. Эти параметры указывают способ форматирования даты и времени, элементы сортируются в алфавитном порядке, строки сравниваются и так далее.|
|**Службы OLE DB**|Указывает битовую маску, которая указывает службы OLE DB, чтобы включить или отключить.|
|**строки**|Указывает, следует ли запрашивать пользователя во время установления соединения.|
|**Расширенные свойства**|Строка, содержащая поставщика, расширенные сведения о соединении. Это свойство используется только для подключения к конкретному поставщику данных, которые не может быть описан через механизм свойства.|

## <a name="see-also"></a>См. также
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [свойство поставщика (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [объекта набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
