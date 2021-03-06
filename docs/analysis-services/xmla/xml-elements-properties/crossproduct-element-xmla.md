---
title: Элемент CrossProduct (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 07e34958589bd9366cda6b42207c289bfda72453
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="crossproduct-element-xmla"></a>Элемент CrossProduct (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит перекрестное произведение упорядоченных множеств элементов из каждой иерархии для [оси](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) элемент, который использует [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) тип данных, возвращенных [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Axis>  
   ...  
   <CrossProduct Size="integer">  
      <Members>...</Members>  
   </CrossProduct>  
   ...  
</Axis>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Оси](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|Дочерние элементы|[Члены](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|Attribute|Описание|  
|---------------|-----------------|  
|Размер|Требуется **целое** атрибута. Указывает число кортежей, содержащихся в перекрестное произведение, представленного **CrossProduct** элемента.|  
  
## <a name="remarks"></a>Примечания  
 Когда клиентское приложение задает **AxisFormat** свойства *ClusterFormat*, элементы на каждой оси разделяются на кластеры, в которых каждый кластер представляет перекрестное произведение упорядоченных наборов элементов из каждой иерархии. Каждый кластер представляется **CrossProduct** элемента. Каждый **CrossProduct** элемент содержит **члены** элемента каждой иерархии на оси. Объект **CrossProduct** элемент может содержать элементы из одной иерархии.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует структуру **CrossProduct** элемент, если клиент указывает *ClusterFormat* для **AxisFormat** свойства XMLA, учитывая следующие элементы для оси:  
  
||||||  
|-|-|-|-|-|  
|Иерархия **Time**|1999|1999|2000|2001|  
|Иерархия **Category**|Actual|Budget|Budget|Budget|  
|Clusters|Кластер 1|Кластер 1|Кластер 1|Кластер 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size="4">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
      <CrossProduct Size="1">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[2001]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>См. также:  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
