---
title: Задача "Файловая система" для Azure Data Lake Store | Документы Майкрософт
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: control-flow
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.openlocfilehash: e1331900994e61eacb66d0cc4efe5e49fc20e508
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="azure-data-lake-store-file-system-task"></a>Задача "Файловая система" для Azure Data Lake Store

Задача "Файловая система" для Azure Data Lake Store позволяет пользователям выполнять различные операции файловой системы в [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Компонент задачи "Файловая система" для Azure Data Lake Store входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

## <a name="configure-the-azure-data-lake-store-file-system-task"></a>Настройка задачи "Файловая система" для Azure Data Lake Store

Чтобы добавить в пакет задачу "Файловая система" для Azure Data Lake Store, перетащите ее с панели элементов служб SSIS на панель холста конструктора. Затем дважды щелкните задачу или щелкните ее правой кнопкой мыши и выберите команду **Изменить**, чтобы открыть диалоговое окно **редактора задачи "Файловая система" для Azure Data Lake Store**.

Операция файловой системы, которая будет выполнена, задается свойством **Операция**. Выберите одну из следующих операций:

- **CopyToADLS**. Загрузка файлов в ADLS.
- **CopyFromADLS**. Скачивание файлов из ADLS.

## <a name="configure-the-properties-for-the-operation"></a>Настройка свойств операции
Для любой операции необходимо указать диспетчер подключений Azure Data Lake.

Ниже приведены свойства, относящиеся к каждой операции:

### <a name="copytoadls"></a>CopyToADLS
- **LocalDirectory**. Задает каталог локального источника, в котором содержатся загружаемые файлы.
- **FileNamePattern**. Определяет фильтр имен для исходных файлов. Загружаются только те файлы, имя которых соответствует указанному шаблону. Поддерживаются подстановочные знаки `*` и `?`.
- **SearchRecursively**. Указывает, следует ли выполнять рекурсивный поиск файлов для загрузки в каталоге источника.
- **AzureDataLakeDirectory**. Указывает каталог назначения ADLS, в который будут загружены файлы.
- **FileExpiry**. Задает дату и время истечения срока действия для файлов, загруженных в ADLS. Если файлы не имеют срока действия, оставьте это свойство пустым.

### <a name="copyfromadls"></a>CopyFromADLS
- **AzureDataLakeDirectory**. Указывает каталог источника ADLS, в котором содержатся файлы для скачивания.
- **SearchRecursively**. Указывает, следует ли выполнять рекурсивный поиск файлов для скачивания в каталоге источника.
- **LocalDirectory**. Указывает каталог назначения, в который будут сохранены скачанные файлы.
