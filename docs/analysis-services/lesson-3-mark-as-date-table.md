---
title: 'Урок 4: Пометить как таблицу дат | Документы Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77f29250621485f5606a0bf33615e8d15eb7d80b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="lesson-3-mark-as-date-table"></a>Занятие 3: Пометить как таблицу дат
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На занятии 2: Добавление данных, вы импортировали таблицу измерения с именем DimDate. Хотя в модели эта таблица называется DimDate, он также может называться как *таблицу дат*, они содержат данные даты и времени.  
  
Всякий раз при использовании функции логики операций со временем DAX в вычислениях, как будет выполняться при создании мер немного позже, необходимо указать свойства таблицы даты, включающие *таблицу дат* и уникальный идентификатор *даты столбец* в этой таблице.
  
На этом занятии вы пометить таблицы DimDate как *таблицу дат* и столбец даты (в таблице дат) в качестве *столбец даты* (идентификатор).  

Прежде чем мы пометить таблицы дат и столбец дат, нам нужно немного обслуживания, чтобы лучше понять нашей модели. Вы заметите таблицы DimDate столбец с именем **FullDateAlternateKey**. Он содержит по одной строке на каждый день каждого календарного года, включается в таблицу. Мы будем использовать этот столбец много формулы мер и в отчетах. Но FullDateAlternateKey не очень хорошо идентификатора для этого столбца. Мы будем переименуйте его в **Дата**, упрощая процесс идентификации и включать в формулы. Когда это возможно, рекомендуется переименовать объекты, такие как таблицы и столбцы, чтобы упростить их идентификацию в клиентские приложения, такие как Power BI и Excel. 
  
Предполагаемое время выполнения данного занятия: **3 минуты**  
  
## <a name="prerequisites"></a>предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [Lesson 2: Добавление данных](../analysis-services/lesson-2-add-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Переименование столбца FullDateAlternateKey

1.  В конструкторе моделей щелкните **DimDate** таблицы.

2.  Дважды щелкните заголовок для **FullDateAlternateKey** столбца и переименуйте его в **даты**.

  
### <a name="to-set-mark-as-date-table"></a>Параметр «Пометить как таблицу данных» (Mark as Date Table)  
  
1.  Выберите столбец **Дата** , а затем убедитесь, что в окне **Свойства** в разделе **Тип данных**выбран тип  **Дата** .  
  
2.  Откройте меню **Таблица** , выберите пункт **Дата**, а затем пункт **Пометить как таблицу дат**.  
  
3.  В диалоговом окне **Пометить как таблицу дат** в списке **Дата** выберите столбец **Дата** в качестве уникального идентификатора. Оно обычно выбирается по умолчанию. Нажмите кнопку **ОК**. 

    ![как табличные lesson3-Дата таблицы](../analysis-services/media/as-tabular-lesson3-date-table.png)
  

## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [занятия 4: Создание связей](../analysis-services/lesson-4-create-relationships.md).
  
