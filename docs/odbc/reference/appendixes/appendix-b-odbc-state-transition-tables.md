---
title: "Приложение б. таблицы перехода состояний ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- state transitions [ODBC]
- transitioning states [ODBC], about state transitions
- state transitions [ODBC], about state transitions
ms.assetid: 15088dbe-896f-4296-b397-02bb3d0ac0fb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 775c3d0464443d11b833a230591b94293343086b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="appendix-b-odbc-state-transition-tables"></a>Приложение б. таблицы перехода состояний ODBC
В таблицах в этом приложении показано, как функции ODBC вызывают переходы среды, подключения, инструкции и дескриптора состояний. Состояние среды, подключения, инструкции и дескриптора обычно указывает, когда можно вызывать функции, использующие соответствующий тип дескриптора (среды, соединения, оператор или дескриптор). Состояния среды, подключения, инструкции и дескриптора перекрываться примерно, как показано на следующем рисунке. Например точное совпадение подключение состояния C5 и C6 и инструкция подтверждает, что S1 через S12 является данных зависит от источника, с момента начала транзакции в различные моменты времени в разных источниках данных и зависит от состояния дескриптор D1i (неявно выделить дескриптор) на состоянии инструкции, с которой связан дескриптор при этом состояние D1e (явно выделить дескриптор) — независимо от состояния любого оператора. Описание каждого состояния см. в разделе [среда переходит](../../../odbc/reference/appendixes/environment-transitions.md), [переходы подключения](../../../odbc/reference/appendixes/connection-transitions.md), [переходы инструкции](../../../odbc/reference/appendixes/statement-transitions.md), и [переходы дескриптора ](../../../odbc/reference/appendixes/descriptor-transitions.md)далее в этом приложении.  
  
 Следующим Перекрытие состояний среды и соединения:  
  
 ![Перекрытие состояний среды и соединения](../../../odbc/reference/appendixes/media/app01.gif "app01")  
  
 Следующим Перекрытие состояний инструкции и соединения:  
  
 ![Инструкции и соединения состояния перекрытие](../../../odbc/reference/appendixes/media/app02.gif "app02")  
  
 Следующим Перекрытие состояний инструкции и дескриптора:  
  
 ![Инструкции и дескриптора состояния перекрытие](../../../odbc/reference/appendixes/media/app03.gif "app03")  
  
 Следующим Перекрытие состояний соединения и дескриптора:  
  
 ![Соединения и дескриптора состояния перекрытие](../../../odbc/reference/appendixes/media/app04.gif "app04")  
  
 Каждая запись в таблицу переходов может принимать одно из следующих значений:  
  
-   **--**— Состояние не изменяется после выполнения функции.  
  
-   **E**  
     ***n***, * *C*n***, * *S*n***, или * *D*n*** — состояние среды, соединения, оператор или дескриптор перемещается в указанное состояние.  
  
-   **(СИСТЕМЫ) ** — В функцию был передан недопустимый дескриптор. Если дескриптор был дескриптор null или является допустимым дескриптором неверного типа — например, дескриптор подключения была передана при требовалось дескриптор инструкции, функция возвращает SQL_INVALID_HANDLE; в противном случае поведение не определено и, возможно, Неустранимая ошибка. Эта ошибка отображается только в том случае, когда это возможно только результат вызова функции в указанном состоянии. Эта ошибка не изменяет состояние и всегда обнаружен диспетчером драйверов, как указано в скобках.  
  
-   **NS** — следующее состояние. Оператор перехода одинаково как если бы инструкция не вышли через асинхронные состояния. Предположим, например, инструкцию, которая создает результирующий набор переходит в состояние S11 из состояния S1 поскольку **SQLExecDirect** возвращается значение SQL_STILL_EXECUTING. Нотация NS в состоянии S11 означает, что переходы для инструкции идентичны таковым для инструкции в состоянии S1, создает результирующий набор. Если **SQLExecDirect** возвращает ошибку, остается в состоянии S1, инструкция; в случае успеха инструкцию переходит в состояние S5; Если это необходимо, инструкцию переходит в состояние S8; и если он выполняется по-прежнему остается в состоянии S11.  
  
-   ***XXXXX*** или * *(*XXXXX*) ** — SQLSTATE, относящемся к таблице перехода. Атрибуты SQLSTATE обнаружил диспетчером драйверов заключаются в круглые скобки. Функция вернула значение SQL_ERROR и указанным SQLSTATE, но не изменяет состояние. Например если **SQLExecute** вызывается перед **SQLPrepare**, возвращается значение SQLSTATE HY010 (функция ошибка последовательности).  
  
> [!NOTE]  
>  Таблицы не содержат ошибок, не относящуюся к перехода таблиц, которые не изменяют состояние. Например, если **SQLAllocHandle** вызывается в состоянии окружения E1 и возвращает SQLSTATE HY001 (ошибка выделения памяти), среда остается в состоянии E1; это не показано в таблице переход среды для ** SQLAllocHandle**.  
  
 Если среда, соединения, оператор или дескриптора можно переместить более одного состояния, показаны все возможные состояния и один или несколько обычных объясните условия, при которых выполняется каждый переход. Следующие сноски могут отображаться в любой таблице.  
  
|Сноска|Значение|  
|--------------|-------------|  
|b|До или после. Курсор был установлен перед началом результирующего набора, или в конце результирующего набора.|  
|с|Текущая функция. Текущая функция выполнялась асинхронно.|  
|d|Требуются данные. Функция вернула значение SQL_NEED_DATA.|  
|Д.|Ошибка. Функция возвращает значение SQL_ERROR.|  
|i|Недопустимая строка. Курсор был установлен на строки в результирующем наборе и либо строка была удалена, или возникла ошибка в операции в строке. Если существует массив состояния строк, значение в массиве строк состояния для строки было SQL_ROW_DELETED или SQL_ROW_ERROR. (Массив состояния строк ссылается атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR.)|  
|NF|Не найден. Функция вернула значение SQL_NO_DATA. Это не применяется, когда **SQLExecDirect**, **SQLExecute**, или **SQLParamData** вернула значение SQL_NO_DATA, после выполнения которой производится поиск инструкцией обновления или удаления.|  
|np|Не подготовлена. Инструкция не подготовлена.|  
|nr|Нет результатов. Инструкция не будет или создано не результирующий набор.|  
|o|Другие функции. Другая функция выполнялась асинхронно.|  
|p|Подготовить. Инструкция была подготовлена.|  
|r|Результаты. Инструкция будет или была создана (возможно, пустой) результирующего набора.|  
|s|Успешно. Функция вернула значение SQL_SUCCESS_WITH_INFO или SQL_SUCCESS.|  
|v|Допустимую строку. Курсор был установлен для строки в результирующем наборе и строки успешно вставлены, успешно обновлен, или другая операция в строке успешно завершена. Если существует массив состояния строк, значение в массиве строк состояния для строки было SQL_ROW_ADDED, SQL_ROW_SUCCESS или SQL_ROW_UPDATED. (Массив состояния строк ссылается атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR.)|  
|x|Выполняющиеся. Функция вернула значение SQL_STILL_EXECUTING.|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 В этом примере таблица строк при переходе состояний среды для **SQLFreeHandle** при *HandleType* SQL_HANDLE_ENV является следующим образом.  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Выделенные|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(СИСТЕМЫ)|E0|(HY010)|  
  
 Если **SQLFreeHandle** вызывается в состоянии среды E0 с *HandleType* значение SQL_HANDLE_ENV, диспетчер драйверов возвращает SQL_INVALID_HANDLE. Если метод вызывается в состоянии E1 с *HandleType* значение SQL_HANDLE_ENV, среде перемещает E0 состояние, если функция завершается успешно и остается в состоянии E1, если функция завершается с ошибкой. Если метод вызывается в состоянии E2 с *HandleType* значение SQL_HANDLE_ENV, диспетчер драйверов всегда возвращает значение SQL_ERROR и SQLSTATE HY010 (функция ошибка последовательности) и среды остается в состоянии E2.  
  
 Чтобы понять таблицы переход состояния, необходимо понимать, какой элемент (среда, соединения, оператор или дескриптор) они ссылаются. Предположим, что функция принимает дескриптор элемента типа X. Таблица переходов между состояниями X для этой функции описывается, как вызывающий влияние на функцию, с дескриптором типа X, элемент этого элемента. Например **SQLDisconnect** принимает дескриптор соединения. Таблица переходов между состояниями соединения для **SQLDisconnect** описывает способ **SQLDisconnect** влияет на состояние соединения, для которого он вызван.  
  
 Предположим, что функция принимает дескриптор элемента типа Y, где Y не равно X. Таблица переходов между состояниями X для этой функции описывает способ вызова функции с дескриптором типа X, связанный с элементом типа Y, оказывает влияние на элемент типа Y. Например, инструкция таблица переходов между состояниями для **SQLDisconnect** описывает как **SQLDisconnect** влияет на состояние при вызове с дескриптором подключение, с которым инструкции оператор связан.  
  
 Это приложение содержит следующие разделы.  
  
-   [Среда переходит](../../../odbc/reference/appendixes/environment-transitions.md)  
  
-   [Переходы подключения](../../../odbc/reference/appendixes/connection-transitions.md)  
  
-   [Инструкция переходов](../../../odbc/reference/appendixes/statement-transitions.md)  
  
-   [Дескриптор переходов](../../../odbc/reference/appendixes/descriptor-transitions.md)