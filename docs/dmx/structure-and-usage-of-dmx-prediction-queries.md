---
title: Структура и использовании прогнозирующих запросов расширений интеллектуального анализа данных | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- prediction joins [DMX]
- empty prediction joins [DMX]
- natural prediction joins [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- queries [DMX], prediction queries
- singleton query predictions [DMX]
- Data Mining Extensions [Analysis Services], prediction queries
ms.assetid: 098bdaa6-9e7d-4e13-a9aa-eb17ce1750e6
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6f4e5d0f723851776340d3435c05e382c88552ae
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="structure-and-usage-of-dmx-prediction-queries"></a>Структура и методы использования прогнозирующих запросов расширений интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  В [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], прогнозирующий запрос можно использовать в расширениях интеллектуального анализа данных (DMX) для прогнозирования неизвестных значений столбцов в новом наборе данных на основе результатов модели интеллектуального анализа данных.  
  
 Тип используемого запроса зависит от того, какие данные необходимо получить от модели. Если требуется создавать простые прогнозы в режиме реального времени, например соответствует ли потенциальный заказчик на веб-сайте «портрету» покупателя велосипеда, то следует использовать одноэлементный запрос. Если необходимо создать пакет прогнозов из набора вариантов, содержащихся в источнике данных, нужно использовать нормальный прогнозирующий запрос.  
  
## <a name="prediction-types"></a>Типы прогнозов  
 С помощью расширений интеллектуального анализа данных можно создавать следующие типы прогнозов.  
  
 Прогнозируемое соединение  
 Используется для создания прогнозов по входным данным на основе существующих шаблонов модели интеллектуального анализа данных. Эту инструкцию запроса должен следовать **ON** предложение, указывающее условия соединения между столбцами модели интеллектуального анализа данных и входных столбцов.  
  
 Естественное прогнозируемое соединение  
 Используется для создания прогнозов на основе имен столбцов модели интеллектуального анализа данных, точно совпадающих с именами столбцов таблицы, по которой выполняется запрос. Эта инструкция запроса не требует **ON** предложение, так как условие соединения автоматически создается на основе совпадающих имен между столбцами модели интеллектуального анализа данных и входными столбцами.  
  
 Пустое прогнозируемое соединение  
 Используется для получения наиболее вероятного прогноза без необходимости указания входных данных. При этом возвращается прогноз на основе исключительно содержимого модели интеллектуального анализа данных.  
  
 Одноэлементный запрос  
 Используется для создания прогноза путем указания данных запросу. Это полезная инструкция, так как она позволяет указать запросу единственный вариант и быстро получить результат. Например, с помощью запроса можно спрогнозировать вероятность покупки велосипеда лицом женского пола в возрасте 35 лет, состоящем в браке. Этому запросу не требуется внешний источник данных.  
  
## <a name="query-structure"></a>Структура запроса  
 Для построения прогнозирующего запроса в расширениях интеллектуального анализа данных используется комбинация следующих элементов:  
  
-   **ВЫБЕРИТЕ [ПЛОСКИМ]**  
  
-   **TOP**  
  
-   **ИЗ***\<модели >***PREDICTION JOIN**   
  
-   **ON**  
  
-   **WHERE**  
  
-   **ORDER BY**  
  
 **ВЫБЕРИТЕ** элемент прогнозирующего запроса определяет столбцы и выражения, которые будут отображаться в результатах, а может включать следующие данные:  
  
-   **Прогноз** или **PredictOnly** столбцы из модели интеллектуального анализа данных.  
  
-   Любой столбец входных данных, используемый при создании прогнозов.  
  
-   Функции, возвращающие столбец данных.  
  
 **FROM**  *\<модели >* **PREDICTION JOIN** элемент определяет исходные данные для использования при создании прогноза. Для одноэлементного запроса — это последовательность значений, назначенных столбцам. Для пустого прогнозируемого соединения оставляется пустое значение.  
  
 **ON** элемент сопоставляет столбцы, которые определены в модели интеллектуального анализа данных со столбцами внешнего набора данных. При создании запроса пустого прогнозируемого соединения или естественного прогнозируемого соединения этот элемент включать не требуется.  
  
 Можно использовать **ГДЕ** предложение для фильтрации результатов прогнозирующего запроса. Можно использовать **ВЕРХНЕЙ** или **ORDER BY** предложение для выбора наиболее вероятных прогнозов. Дополнительные сведения об использовании этих предложений см. в разделе [ВЫБЕРИТЕ &#40;расширений интеллектуального анализа данных&#41;](../dmx/select-dmx.md).  
  
 Дополнительные сведения о синтаксисе инструкции прогноза см. в разделе [SELECT FROM &#60;модели&#62; PREDICTION JOIN &#40;расширений интеллектуального анализа данных&#41; ](../dmx/select-from-model-prediction-join-dmx.md) и [SELECT FROM &#60;модели&#62; &#40;расширений интеллектуального анализа данных &#41;](../dmx/select-from-model-dmx.md).  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных & #40; расширений интеллектуального анализа данных & #41; Ссылка](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; функции ссылки](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных & #40; расширений интеллектуального анализа данных & #41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; синтаксические обозначения](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; элементы синтаксиса](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Общие сведения об инструкции SELECT в расширении интеллектуального анализа данных](../dmx/understanding-the-dmx-select-statement.md)  
  
  
