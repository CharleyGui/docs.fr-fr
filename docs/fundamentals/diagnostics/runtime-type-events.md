---
title: Événements d’exécution du système de type
description: Consultez événements du Runtime .NET qui recueillent des informations de diagnostic spécifiques au système de type .NET, telles que TypeLoadStart et TypeLoadStop.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96588593"
---
# <a name="net-runtime-type-events"></a>Événements de type .NET Runtime

Ces événements collectent des informations relatives au chargement des types. Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)

## <a name="typeloadstart-event"></a>Événement TypeLoadStart

|Mot clé pour déclencher l'événement|Événement|Level|  
|-----------------------------------|-----------|-----------|  
|`TypeDiagnosticKeyword` (0x8000000000)|Informatif (4)|  

|Événement|ID de l’événement|Description|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|73|Un chargement de type a démarré.|

|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|ID de l’opération de chargement de type.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|  

## <a name="typeloadstop-event"></a>Événement TypeLoadStop

|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|-----------|  
|`TypeDiagnosticKeyword` (0x8000000000)|Informatif (4)|  

|Événement|ID de l’événement|Description|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|74|Une charge de type est terminée.|

|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|ID de l’opération de chargement de type (correspond au TypeLoadStartID de l’événement TypeLoadStart correspondant).|
|`LoadLevel`|`win:UInt16`|Tapez le niveau de charge.|
|`TypeID`|`win:UInt64`|Pointeur vers le handle de type.|
|`TypeName`|`win:UnicodeString`|Nom du type.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l'instance de CLR ou CoreCLR.|  
