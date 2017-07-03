---
title: "Область выражения для итогов, статистических функций и встроенных коллекций | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8d24287-8557-4b03-bea7-ca087f449b62
caps.latest.revision: 11
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d713c0c3cf84bb17e0a2bd318a2b59179fa5edf9
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="expression-scope-for-totals-aggregates-and-built-in-collections"></a>Область выражения для суммирования, агрегатных функций и встроенных коллекций
  Термин *область* используется в нескольких контекстах, что становится понятно при написании выражений. Область может указывать на данные, используемые для вычисления выражений, набор текстовых полей на подготавливаемой странице, набор элементов отчета, которые могут отображаться или быть скрытыми. Термин *область* используется в разделах о вычислении выражений, синтаксисе агрегатных функций, условной видимости и в сообщениях об ошибках, связанных с этими темами. Ниже приводится описание различий в употреблении термина *область* .  
  
-   **Область данных** . Иерархия областей, используемых обработчиком отчетов при объединении данных и макета отчета для построения областей данных, например таблиц и диаграмм, в которых отображаются данные. Знание области данных помогает достичь ожидаемого результата при следующих действиях.  
  
    -   **Написание выражений с агрегатными функциями** . Определяет агрегируемые данные. Расположение выражения в отчете влияет на то, какие данные оказываются в области для статистического вычисления.  
  
    -   **Добавление sparkline-графиков в таблицу или матрицу** . Определяет границы диапазонов для осей диаграммы для выравнивания вложенных экземпляров в таблице или матрице.  
  
    -   **Добавление индикаторов в таблицу или матрицу** . Определяет минимальный и максимальный масштаб датчиков для выравнивания вложенных экземпляров в таблице или матрице.  
  
    -   **Написание выражений сортировки** . Определяют включающую область, которую можно использовать для синхронизации порядка сортировки нескольких связанных элементов отчета.  
  
-   **Область ячейки** . Набор групп строк и столбцов в области данных табликса, к которой принадлежит ячейка. По умолчанию в каждой ячейке табликса есть текстовое поле. Значением текстового поля является выражение. Положение ячейки косвенно определяет область данных, которая может быть указана в выражении для статистического вычисления.  
  
-   **Область элементов отчета** . Указывает набор элементов на подготовленной странице отчета. Обработчик отчетов объединяет данные и элементы макета отчета для получения скомпилированного определения отчета. Во время этого процесса области данных, например таблицы или матрицы, расширяются таким образом, чтобы показать все данные отчета. После этого скомпилированный отчет обрабатывается модулем подготовки отчета. Модуль подготовки отчета определяет, какие элементы отчета будут показаны на каждой странице. На сервере отчетов каждая страница подготавливается при просмотре. При экспорте отчета к просмотру подготавливаются все страницы. Знание области элементов отчета помогает достичь ожидаемого результата при следующих действиях.  
  
    -   **Добавление переключаемых элементов** . Определяет текстовое поле для добавления переключателя, управляющего видимостью элемента отчета. Переключатель можно добавлять только для текстовых полей, находящихся в области соответствующего элемента отчета.  
  
    -   **Написание выражений в верхних и нижних колонтитулах страницы** . Определяет значения в выражениях в текстовых полях или других элементах отчета, отображающихся на подготовленной странице.  
  
 Знание областей помогает правильно писать выражения для получения ожидаемого результата.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="DataScope"></a> Общие сведения об области данных и иерархии данных  
 Область данных задает набор данных для отчета. У области данных имеется естественная иерархия со свойственным ей отношением включения. Области, расположенные выше в иерархии, содержат области, расположенные ниже в иерархии. Следующий список областей данных описывает иерархию по убыванию количества данных.  
  
-   **Наборы данных после применения фильтров** . Определяет набор данных отчета, связанный с областью данных или элементом отчета в тексте отчета. Данные для статистической обработки берутся из набора данных отчета после применения к ним критериев фильтра. Для общих наборов данных это означает как фильтры в определении общих наборов данных, так и фильтры в экземплярах наборов данных в отчете.  
  
-   **Области данных** . Задает данные из области данных после применения к ним фильтра и выражений сортировки. При вычислении агрегатов для областей данных групповые фильтры не используются.  
  
-   **Группы областей данных после применения фильтров группы** . Определяет данные после применения выражений группы и фильтров группы к родительской и дочерним группам. Для таблицы это группы строк и столбцов. Для диаграммы это группы рядов и категорий. Для идентификации вложенности области каждая родительская группа содержит дочернюю группу.  
  
-   **Вложенные области данных** Определяют данные для вложенной области данных в контексте ячейки, к которой они добавляются после применения фильтра вложенной области данных и выражений сортировки.  
  
-   **Группы строк и столбцов для вложенных областей данных** . Определяет данные после применения выражений группы вложенной области данных и групповых фильтров.  
  
 Знание иерархии областей важно при написании выражений с агрегатными функциями.  
  
##  <a name="Aggregates"></a> Выражения и область ячейки  
 При указании области определяются данные, которые обработчик отчетов будет использовать при статистическом вычислении. В зависимости от выражения и расположения выражения правильная область может быть *включающей областью*(родительской областью) или *включенной областью*(дочерней или вложенной областью). Обычно нельзя указать отдельный экземпляр группы при статистическом вычислении. Можно указать статистическую обработку для всех экземпляров группы.  
  
 Когда обработчик отчетов комбинирует данные из набора данных отчета с областью данных табликса, он вычисляет выражения группы и создает строки и столбцы, необходимые для представления экземпляров группы. Значение выражений в текстовом поле для каждой ячейки табликса вычисляется в контексте области ячейки. В зависимости от структуры табликса ячейка может принадлежать нескольким группам строк или столбцов. Для агрегатных функций можно указать используемую область с помощью одной из следующих областей:  
  
-   **Область по умолчанию** . Данные, входящие в область для вычисления, во время обработки выражения обработчиком отчетов. Область по умолчанию — это набор групп с наивысшим уровнем вложения, к которому принадлежит ячейка или точка данных. Для области данных табликса этот набор групп может включать группы строк и столбцов. Для диаграммной области данных этот набор может включать группы категорий и рядов.  
  
-   **Именованная область** Имя набора данных, области данных или группы области данных, входящих в область выражения. Для статистического вычисления можно указать включающую область. Нельзя в одном выражении указать именованную область как для групп строк, так и для групп столбцов. Нельзя указать включенную область, если выражение не используется для вложенной статистической обработки.  
  
     Следующее выражение создает годы интервала между SellStartDate и LastReceiptDate. Эти поля находятся в разных наборах данных — DataSet1 и DataSet2. [Функция First (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-first-function.md), агрегатная функция, возвращает первое значение SellStartDate в DataSet1 и первое значение LastReceiptDate в DataSet2.  
  
    ```  
    =DATEDIFF(“yyyy”, First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   **Доменная область** . Область синхронизации. Тип области данных, применяемой к вычислению выражения для вложенных областей данных. Доменная область используется для указания агрегатов среди всех экземпляров группы, что позволяет легко выравнивать и сравнивать вложенные экземпляры. Например, можно выровнять диапазон и высоту для sparkline-графиков в таблице так, что значения будут идти параллельно.  
  
 В некоторых местах отчетах необходимо указать область. Например, для текстового поля в области конструктора необходимо указать имя используемого набора данных: `=Max(Fields!Sales.Value,"Dataset1")`. В других местах это будет неявно заданная область по умолчанию. Например, если для текстового поля в области группы не будет задан агрегат, будет использована статистическая функция First.  
  
 Во всех разделах по агрегатным функциям указаны области, допустимые для их использования. Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md).  
  
##  <a name="Examples"></a> Примеры статистических выражений для табличной области данных  
 Для написания выражений, которые задают области, не являющиеся областями по умолчанию, требуется практика. Сведения о различных областях приведены на следующем рисунке и таблице. На рисунке показана каждая ячейка в таблице данных по продажам, показывающей количество всех проданных товаров за год и за квартал по месту продажи. Обратите внимание на визуальные метки на дескрипторах строки и столбца, которые отображают структуру групп строк и столбцов, указывая вложенные группы. Таблица имеет следующую структуру:  
  
-   Заголовок таблицы, содержащий угловую ячейку и три строки, включающие в себя заголовки групп столбцов.  
  
-   Две вложенные группы строк, связанные с категорией Cat и подкатегорией SubCat.  
  
-   Две вложенные группы столбцов, связанные с годом Year и кварталом Qtr.  
  
-   Один столбец со статическими итоговыми значениями под названием Totals.  
  
-   Одна смежная группа столбцов, связанная с местами продаж Territory.  
  
 Заголовок столбца для территориальной группы разбит на две ячейки для удобства просмотра. Первая ячейка показывает название территории и суммы продаж, а вторая ячейка содержит текст заполнителя, который вычисляется как доля каждой территории в общих продажах.  
  
 ![rs_BasicTableSumCellScope](../../reporting-services/report-design/media/rs-basictablesumcellscope.gif "rs_BasicTableSumCellScope")  
  
 Пусть набор данных — это DataSet1 и таблица — это Tablix1. В следующей таблице указаны метка ячейки, область по умолчанию и примеры. Значения для текста заполнителя показаны в синтаксисе выражения.  
  
|Ячейка|Область по умолчанию|Метка заполнителя|Текст или значение заполнителя|  
|----------|-------------------|------------------------|--------------------------------|  
|C01|Tablix1|[Sum(Qty)]|Агрегаты и область<br /><br /> `=Sum(Fields!Qty.Value)`|  
|C02|Внешняя группа столбцов "Year"|[Year]<br /><br /> ([YearQty])|`=Fields!Year.Value`<br /><br /> `=Sum(Fields!Qty.Value)`|  
|C03|Tablix1|[Sum(Qty)]|Totals<br /><br /> `=Sum(Fields!Qty.Value)`|  
|C04|Группа соседних столбцов "Territory"|([Total])|Territory<br /><br /> `=Sum(Fields!Qty.Value)`|  
|C05|Внутренняя группа "Qtr"|[Qtr]<br /><br /> ([QtrQty])|Q<br /><br /> `=Fields!Qtr.Value`<br /><br /> `=Sum(Fields!Qty.Value)`|  
|C06|Группа соседних столбцов "Territory"|[Territory]<br /><br /> ([Tty])<br /><br /> [Pct]|`=Fields!Territory.Value`<br /><br /> `=Sum(Fields!Qty.Value)`<br /><br /> `=FormatPercent(Sum(Fields!Qty.Value,"Territory")/Sum(Fields!Qty.Value,"Tablix1"),0) & " of " & Sum(Fields!Qty.Value,"Tablix1")`|  
|C07|Внешняя группа строк "Cat"|[Cat]<br /><br /> [Sum(Qty)]|`=Fields!Cat.Value`<br /><br /> `=Sum(Fields!Qty.Value)`|  
|C08|Совпадает с C07|||  
|C09|Внешняя группа строк "Cat" и внутренняя группа столбцов "Qtr"|[Sum(Qty)]|`=Sum(Fields!Qty.Value)`|  
|C10|Совпадает с C07|<\<Expr >>|`=Sum(Fields!Qty.Value) & ": " & FormatPercent(Sum(Fields!Qty.Value)/Sum(Fields!Qty.Value,"Tablix1"),0) & " of " & Sum(Fields!Qty.Value,"Tablix1")`|  
|C11|Внешняя группа строк "Cat" и группа столбцов "Territory"|<\<Expr >>|`=Sum(Fields!Qty.Value) & ": " & FormatPercent(Sum(Fields!Qty.Value)/Sum(Fields!Qty.Value,"Territory"),0) & " of " & Sum(Fields!Qty.Value,"Territory")`|  
|C12|Внутренняя группа строк "Subcat"|[Subcat]<br /><br /> [Sum(Qty)]|`=Fields!SubCat.Value`<br /><br /> `=Sum(Fields!Qty.Value)`|  
|C13|Внутренняя группа строк "Subcat" и внутренняя группа столбцов "Qtr"|[Sum(Qty)]|`=Sum(Fields!Qty.Value)`|  
|C14|Внутренняя группа строк "Subcat"|<\<Expr >>|`=Sum(Fields!Qty.Value) & ": " & FormatPercent(Sum(Fields!Qty.Value)/Sum(Fields!Qty.Value,"Cat"),0) & " of " & Sum(Fields!Qty.Value,"Cat")`|  
|C15|Внутренняя группа строк "Subcat" и группа столбцов "Territory"|<\<Expr >>|`=Sum(Fields!Qty.Value) & ": " & FormatPercent(Code.CalcPercentage(Sum(Fields!Qty.Value),Sum(Fields!Qty.Value,"Cat")),0) & " of " & Sum(Fields!Qty.Value,"Cat")`|  
  
 Дополнительные сведения об интерпретации визуальных различий в областях данных табликса см. в разделе [Ячейки, строки и столбцы области данных табликса (построитель отчетов) и службы SSRS](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md). Дополнительные сведения об области данных табликса см. в разделе [Ячейки, строки и столбцы области данных табликса (построитель отчетов) и службы SSRS](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md). Дополнительные сведения о выражениях и статистических функциях см. в разделах [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md) и [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md).  
  
  
##  <a name="Sparklines"></a> Синхронизация шкал для sparkline-графиков  
 Для сравнения значений в разное время по горизонтальной оси в спарклайн-графике, вложенном в таблицу или матрицу, можно синхронизировать значения групп категорий. Это называется выравниванием осей. При выборе варианта с выравниванием осей в отчете автоматически устанавливается минимальное и максимальное значения по осям и предоставляется заполнитель для статистических значений, существующих не в каждой категории. Это приводит к выравниванию значений спарклайн-графика по каждой категории и дает возможность сравнивать значения для каждой строки статистических данных. При выборе этого варианта область вычисления выражения изменяется на *доменную область*. Настройка доменной области для вложенных графиков также косвенно управляет назначением цветов для каждой категории в условных обозначениях.  
  
 Например, предположим, в спарклайн-графике, показывающем недельные тренды, есть данные о продажах для одного города за 3 месяца и для другого города за 12 месяцев. Без синхронизации шкал спарклайн-график для первого города будет иметь только 3 линии, они будут значительно шире и будут занимать столько же места, сколько 12 линий для второго города.  
  
 Дополнительные сведения см. в разделе [Выравнивание данных в диаграмме в таблице или матрице (построитель отчетов и службы SSRS)](../../reporting-services/report-design/align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md).  
  
  
##  <a name="Indicators"></a> Синхронизация диапазонов для индикаторов  
 Для указания значений данных, используемых в наборе индикаторов, необходимо указать область. В зависимости от макета области данных, содержащей индикаторы, указывается область или включающая область. Например, в строке заголовка группы, связанной с категорией продаж, набор стрелок (вверх, вниз, влево, вправо) может показывать объем продаж относительно порогового значения. Включающая область — это имя таблицы или матрицы, содержащих индикаторы.  
  
 Дополнительные сведения см. в разделе [Задание области действия синхронизации (построитель отчетов и службы SSRS)](../../reporting-services/report-design/set-synchronization-scope-report-builder-and-ssrs.md).  
  
  
##  <a name="Page"></a> Указание областей для верхних и нижних колонтитулов  
 Для отображения разных данных на разных страницах отчета добавляются выражения для элементов отчета, которые должны быть на подготовленных для просмотра страницах. Поскольку отчет разбивается на страницы в процессе подготовки к просмотру, определить, какие элементы находятся на странице, можно только во время подготовки. Например, ячейка в строке детализации содержит текстовое поле с множеством экземпляров на странице.  
  
 Для этого существует глобальная коллекция ReportItems. Это набор текстовых полей на текущей странице.  
  
 Дополнительные сведения см. в разделах [Верхние и нижние колонтитулы страницы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md) и [Ссылки на коллекцию ReportItems (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-reportitems-collection-references-report-builder.md).  
  
  
##  <a name="Toggles"></a> Указание переключаемых элементов для углубленной детализации и условной видимости  
 Переключатель — это изображение плюса или минуса, добавляемое к текстовому полю, которое можно щелкнуть для того, чтобы отобразить или спрятать другие элементы отчета. На странице **Видимость** для большинства свойств элементов отчета можно добавить переключатель. Переключаемый элемент должен находиться в области включения более высокого уровня, чем элемент, который надо отобразить или скрыть.  
  
 В области данных табликса для создания эффекта углубленной детализации, то есть возможности развернуть таблицу и показать больше данных по щелчку текстового поля, необходимо установить свойство **Видимость** для группы и установить переключатель для текстового поля в заголовке группы, связанной с включающей группой.  
  
 Дополнительные сведения см. в разделе [Добавление действия "Развернуть" или "Свернуть" к элементу (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md).  
  
  
##  <a name="Sort"></a> Указание выражений сортировки для синхронизации порядка сортировки  
 При добавлении кнопки интерактивной сортировки для столбца таблицы можно синхронизовать сортировку для нескольких элементов, имеющих общую включающую область. Например, можно добавить кнопку к заголовку столбца матрицы и указать включающую область в виде названия набора данных, привязанного к матрице. Когда пользователь нажимает кнопку сортировки, сортируются не только строки в матрице, но и группы рядов диаграмм, связанные с тем же набором данных. Таким образом, все области данных, связанные с набором данных, могут быть синхронизированы для отображения в одинаковом порядке сортировки.  
  
 Дополнительные сведения см. в разделе [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
  
##  <a name="Nulls"></a> Подавление значения NULL или нулевых значений в ячейках  
 Во многих отчетах вычисления, выполняемые в областях групп, могут создавать множество ячеек с нулевыми значениями или значениями NULL. Чтобы уменьшить помехи в отчете, добавьте выражение, возвращающее пробелы при нулевых статистических значениях. Дополнительные сведения см. в разделе "Примеры запрета значений NULL и нулевых значений" в статье [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md).  
  
  
## <a name="see-also"></a>См. также  
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Примеры выражений групп (построитель отчетов и службы SSRS)](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)   
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Форматирование текста и заполнителей (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)  
  
  