---
title: Элемент RestrictionList (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 70c42fe34a3ca825087d4965269dda004ef3f886
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="restrictionlist-element-xmla"></a>Элемент RestrictionList (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит коллекцию столбцов ограничений и значений, используемых методом [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Restrictions>  
   <RestrictionList>  
      <!-- Zero or more restriction columns and values -->  
   </RestrictionList>  
</Restrictions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Ограничения](../../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
|Дочерние элементы|Столбцы и значения ограничений (см. примечания).|  
  
## <a name="remarks"></a>Примечания  
 Элемент **RestrictionList** содержит коллекцию столбцов ограничений, которые могут служить в качестве фильтров для данных, возвращаемых методом **Discover** . Каждый столбец ограничений в элементе **RestrictionList** определен с помощью отдельного XML-элемента. Значением столбца ограничений являются данные, содержащиеся в этом XML-элементе, а имя столбца ограничений соответствует имени XML-элемента.  
  
## <a name="see-also"></a>См. также:  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
