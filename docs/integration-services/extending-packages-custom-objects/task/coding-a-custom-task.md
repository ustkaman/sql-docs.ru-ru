---
title: "Программирования пользовательской задачи | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Validate method
- custom tasks [Integration Services], validating
- validation [Integration Services], design-time tasks
- SSIS custom tasks, validating
ms.assetid: dc224f4f-b339-4eb6-a008-1b4fe0ea4fd2
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c4fd06d10d2ecd2796d0b12707c5e34168941c7c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="coding-a-custom-task"></a>Создание кода пользовательской задачи
  После создания класса, наследующего от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.Task>, и применения к нему атрибута <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>, необходимо переопределить реализацию свойств и методов базового класса, чтобы обеспечить пользовательские функциональные возможности.  
  
## <a name="configuring-the-task"></a>Настройка задачи  
  
### <a name="validating-the-task"></a>Проверка задачи  
 При разработке пакета служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] можно использовать проверку, чтобы убедиться в правильности настроек каждой задачи. Проверка позволит отследить неверные или неподходящие настройки сразу же после их задания, вместо того, чтобы обнаруживать их лишь во время выполнения. Цель проверки состоит в том, чтобы определить, содержит ли задача недопустимые настройки или соединения, которые могут помешать ее успешному выполнению. Таким образом, можно убедиться в том, что пакет содержит только те задачи, выполнение которых будет успешным с первой попытки.  
  
 Можно реализовать проверку с помощью **проверки** метода в пользовательском коде. Среда выполнения осуществляет проверку задачи путем вызова **проверки** метода в задаче. Разработчику задачи следует определить критерии успешной или неуспешной проверки задачи, а также обеспечить уведомление обработчика времени выполнения о результатах этой оценки.  
  
#### <a name="task-abstract-base-class"></a>Абстрактный базовый класс Task  
 <xref:Microsoft.SqlServer.Dts.Runtime.Task> Предоставляет абстрактный базовый класс **проверки** метод, переопределяемый каждой задачей для определения условий проверки. [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Автоматически вызывает конструктор **проверки** метода несколько раз во время разработки пакета и предоставляет пользователю визуальные подсказки при возникновении предупреждения или ошибки, для выявления проблем с конфигурацией задачи. Задачи предоставляют результаты проверки, возвращая значение из перечисления <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> и формируя события с предупреждениями и ошибками. Эти события содержат сведения, которые отображаются пользователю в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
 Ниже приведены примеры проверки:  
  
-   Диспетчер соединений проверяет имя определенного файла.  
  
-   Диспетчер соединений проверяет, является ли тип входа ожидаемым типом, например, XML-файлом.  
  
-   Задача, которой на входе необходима база данных, убеждается в невозможности получения данных из подключения, не являющегося подключением к базе данных.  
  
-   Задача убеждается в отсутствии противоречий между заданными для нее свойствами.  
  
-   Задача убеждается в доступности всех необходимых ресурсов, используемых ею во время выполнения.  
  
 Оценивая необходимость проверки тех или иных факторов, следует учитывать производительность системы. Например, входом задачи может быть соединение по сети с низкой пропускной способностью или большим трафиком. При выполнении проверки может потребоваться несколько секунд на обработку, если необходимо проверить доступность ресурса. Еще одна проверка может привести к полном обходу сервера с высокой загрузкой, в результате выполнение проверки замедлится. Хотя можно проверять многие из свойств и настроек, не все они нуждаются в проверке.  
  
-   Код в **проверки** метод также вызывается <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> перед выполнением задач и <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> отменяет выполнение, если проверка не пройдена.  
  
#### <a name="user-interface-considerations-during-validation"></a>Рекомендации по пользовательскому интерфейсу во время проверки  
 <xref:Microsoft.SqlServer.Dts.Runtime.Task> Включает <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> интерфейс в качестве параметра для **проверки** метод. Интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> содержит методы, вызываемые задачей для формирования событий в обработчике среды выполнения. Методы <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> вызываются при возникновении ошибки или выдаче предупреждения во время проверки. Для обоих методов требуются одни и те же параметры. В их число входит код ошибки, исходный компонент, описание, файл справки и данные контекста справки. Конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] использует эти сведения для отображения визуальных подсказок в области конструктора. К визуальным подсказкам, предоставляемым конструктором, относится значок восклицания, который отображается рядом с задачей в области конструктора. Эта визуальная подсказка указывает пользователю на то, что необходима дополнительная настройка задачи прежде, чем ее выполнение может быть продолжено.  
  
 Значок восклицания также отображает подсказку, содержащую сообщение об ошибке. Сообщение об ошибке предоставляется задачей в параметре описания события. Также отображаются сообщения об ошибках в **список задач** области [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], предоставляя пользователю центральное расположение для просмотра всех ошибок проверки.  
  
#### <a name="validation-example"></a>Пример проверки  
 В следующем примере кода показана задача с **UserName** свойство. Это свойство было задано как обязательное для успешного завершения проверки. Если свойство не задано, задача выдает ошибку и возвращает значение <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> из перечисления <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>. **Проверки** метод заключается в блок try/catch и не проходит проверку, если возникает исключение.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class SampleTask : Task  
{  
  private string userName = "";  
  
  public override DTSExecResult Validate(Connections connections,  
     VariableDispenser variableDispenser, IDTSComponentEvents events,  
     IDTSLogging log)  
  {  
    try  
    {  
      if (this.userName == "")  
      {  
        //   Raise an OnError event.  
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0);  
        //   Fail validation.  
        return DTSExecResult.Failure;  
      }  
      //   Return success.  
      return DTSExecResult.Success;  
    }  
    catch (System.Exception exception)  
    {  
      //   Capture exceptions, post an error, and fail validation.  
      events.FireError(0, "Sampletask", exception.Message, "", 0);  
      return DTSExecResult.Failure;  
    }  
  }  
  public string UserName  
  {  
    get  
    {  
      return this.userName;  
    }  
    set  
    {  
      this.userName = value;  
    }  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Public Class SampleTask  
  Inherits Task  
  
  Private _userName As String = ""  
  
  Public Overrides Function Validate(ByVal connections As Connections, _  
     ByVal variableDispenser As VariableDispenser, _  
     ByVal events As IDTSComponentEvents, _  
     ByVal log As IDTSLogging) As DTSExecResult  
  
    Try  
      If Me._userName = "" Then  
        '   Raise an OnError event.  
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0)  
        '   Fail validation.  
        Return DTSExecResult.Failure  
      End If  
      '   Return success.  
      Return DTSExecResult.Success  
    Catch exception As System.Exception  
      '   Capture exceptions, post an error, and fail validation.  
      events.FireError(0, "Sampletask", exception.Message, "", 0)  
      Return DTSExecResult.Failure  
    End Try  
  
  End Function  
  
  Public Property UserName() As String  
    Get  
      Return Me._userName  
    End Get  
    Set(ByVal Value As String)  
      Me._userName = Value  
    End Set  
  End Property  
  
End Class  
```  
  
### <a name="persisting-the-task"></a>Сохранение задачи  
 Как правило, нет необходимости реализовывать для задачи пользовательскую сохраняемость. Нестандартный механизм сохраняемости необходим только в случае, когда свойства объекта используют сложные типы данных. Дополнительные сведения см. в разделе [Разработка пользовательских объектов для служб Integration Services](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md).  
  
## <a name="executing-the-task"></a>Выполнение задачи  
 В этом разделе описывается использование **Execute** метод, который наследуется и переопределяется задачами. В разделе также поясняются различные способы предоставления сведений о результатах выполнения задачи.  
  
### <a name="execute-method"></a>Метод Execute  
 Выполнять задачи, содержащиеся в пакете, когда [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] среды выполнения вызывает их **Execute** метод. Задачи реализуют их основную бизнес-логику и функциональность в этом методе и предоставляют результаты выполнения путем отправки сообщений, возвращая значение из <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> перечисления и переопределяя свойство **получить** из **ExecutionValue** свойство.  
  
 Базовый класс <xref:Microsoft.SqlServer.Dts.Runtime.Task> предоставляет реализацию по умолчанию метода <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>. Пользовательские задачи переопределяют этот метод, чтобы определить собственную функциональность времени выполнения. Объект <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> упаковывает задачу, изолируя ее от обработчика среды выполнения и других объектов в пакете. В результате этой изоляции задача не имеет сведений о своем местоположении в пакете с учетом порядка выполнения. Она выполняется только после вызова средой выполнения. Такая архитектура предотвращает проблемы, которые могут возникнуть при изменении задачами пакета в процессе выполнения. Задаче предоставляется доступ к другим объектам в пакете только через объекты, передаваемые ей в качестве параметров в методе <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>. Эти параметры позволяют задачам вызывать события, делать записи в журнале событий, обращаться к коллекции Variables и прикреплять соединения к источникам данных в транзакциях, одновременно сохраняя изоляцию, которая необходима для обеспечения стабильности и надежности пакета.  
  
 В следующей таблице перечислены параметры, передаваемые задаче в методе <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>.  
  
|Параметр|Description|  
|---------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Connections>|Содержит коллекцию объектов <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>, доступных для задачи.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.VariableDispenser>|Содержит переменные, доступные для задачи. Переменные используются задачами через свойство VariableDispenser, а не напрямую. Свойство VariableDispenser осуществляет блокировку и разблокирование переменных, а также предотвращает взаимоблокировки или перезаписи.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>|Содержит методы, вызываемые задачей для вызова событий в обработчике среды выполнения.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSLogging>|Содержит методы и свойства, используемые задачей для внесения записей в журнал событий.|  
|Объект|Содержит объект транзакции (при наличии такового), частью которого является контейнер. Это значение передается в качестве параметра методу <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.|  
  
### <a name="providing-execution-feedback"></a>Обеспечение обратной связи при выполнении  
 Задачи упаковывают свой код в **try/catch** блоки, чтобы предотвратить возникновение во время выполнения обработчик исключений. Таким образом, гарантируется, что выполнение пакета будет завершено, и не произойдет неожиданной остановки. Однако обработчик среды выполнения предоставляет и другие механизмы обработки ошибок, которые могут возникать во время выполнения задачи. К ним относится выдача сообщений об ошибках и предупреждений, возвращение значения из структуры <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>, выдача сообщений, возвращение значения <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> и раскрытие сведений о результатах выполнения задачи с помощью свойства <xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A>.  
  
 Интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> содержит методы <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A>, которые могут быть вызваны задачей для выдачи сообщений об ошибках и предупреждений в обработчике среды выполнения. Обоим методам требуются такие параметры, как код ошибки, исходный компонент, описание, файл справки и данные контекста справки. В зависимости от конфигурации задачи, среда выполнения отвечает на эти сообщения, вызывая события и точки останова либо записывая данные в журнал событий.  
  
 Объект <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> также предоставляет свойство <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A>, которое можно использовать для предоставления дополнительных сведений о результатах выполнения. Например, если задача удаляет строки из таблицы в рамках его **Execute** метод, он может возвращать количество строк, удаленных в качестве значения <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> свойство. Кроме того, объект <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> предоставляет свойство <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A>. С помощью этого свойства пользователь может сопоставить значение <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A>, возвращаемое задачей, с любой другой переменной, доступной для задачи. Затем указанную переменную можно использовать для настройки элементов управления очередностью между задачами.  
  
### <a name="execution-example"></a>Пример выполнения  
 В следующем примере кода демонстрируется реализация **Execute** метода и переопределенное **ExecutionValue** свойство. Задача удаляет файл, который задается параметром **fileName** свойство задачи. Задача выдает предупреждение, если файл не существует или **fileName** свойства является пустая строка. Эта задача возвращает **логическое** значение в <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> свойство, указывающее, является ли файл был удален.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class SampleTask : Task  
{  
  private string fileName = "";  
  private bool fileDeleted = false;  
  
  public override DTSExecResult Execute(Connections cons,  
     VariableDispenser vars, IDTSComponentEvents events,  
     IDTSLogging log, Object txn)  
  {  
    try  
    {  
      if (this.fileName == "")  
      {  
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0);  
        this.fileDeleted = false;  
      }  
      else  
      {  
        if (System.IO.File.Exists(this.fileName))  
        {  
          System.IO.File.Delete(this.fileName);  
          this.fileDeleted = true;  
        }  
        else  
          this.fileDeleted = false;  
      }  
      return DTSExecResult.Success;  
    }  
    catch (System.Exception exception)  
    {  
      //   Capture the exception and post an error.  
      events.FireError(0, "Sampletask", exception.Message, "", 0);  
      return DTSExecResult.Failure;  
    }  
  }  
  public string FileName  
  {  
    get { return this.fileName; }  
    set { this.fileName = value; }  
  }  
  public override object ExecutionValue  
  {  
    get { return this.fileDeleted; }  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Public Class SampleTask  
  Inherits Task  
  
  Private _fileName As String = ""  
  Private _fileDeleted As Boolean = False  
  
  Public Overrides Function Execute(ByVal cons As Connections, _  
     ByVal vars As VariableDispenser, ByVal events As IDTSComponentEvents, _  
     ByVal log As IDTSLogging, ByVal txn As Object) As DTSExecResult  
  
    Try  
      If Me._fileName = "" Then  
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0)  
        Me._fileDeleted = False  
      Else  
        If System.IO.File.Exists(Me._fileName) Then  
          System.IO.File.Delete(Me._fileName)  
          Me._fileDeleted = True  
        Else  
          Me._fileDeleted = False  
        End If  
      End If  
      Return DTSExecResult.Success  
    Catch exception As System.Exception  
      '   Capture the exception and post an error.  
      events.FireError(0, "Sampletask", exception.Message, "", 0)  
      Return DTSExecResult.Failure  
    End Try  
  
  End Function  
  
  Public Property FileName() As String  
    Get  
      Return Me._fileName  
    End Get  
    Set(ByVal Value As String)  
      Me._fileName = Value  
    End Set  
  End Property  
  
  Public Overrides ReadOnly Property ExecutionValue() As Object  
    Get  
      Return Me._fileDeleted  
    End Get  
  End Property  
  
End Class  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/creating-a-custom-task.md)   
 [Программирования пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/coding-a-custom-task.md)   
 [Разработка пользовательского интерфейса для пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/developing-a-user-interface-for-a-custom-task.md)  
  
  