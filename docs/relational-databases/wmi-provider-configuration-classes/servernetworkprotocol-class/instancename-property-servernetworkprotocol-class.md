---
title: Свойство InstanceName (класс ServerNetworkProtocol) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- InstanceName Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- InstanceName property
ms.assetid: 456911c1-9881-4574-8576-0070eff78c27
caps.latest.revision: 31
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ff9cf626af1fecc516dd14f95b1651ce9612c8b1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="instancename-property-servernetworkprotocol-class"></a>Свойство InstanceName (класс ServerNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает имя экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на который ссылается сетевой протокол сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.InstanceName [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса ServerNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) , который представляет сетевой протокол, используемый экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Строковое значение, определяющее имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], на который ссылается сетевой протокол сервера.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Настройка сетевых протоколов сервера и сетевых библиотек](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
