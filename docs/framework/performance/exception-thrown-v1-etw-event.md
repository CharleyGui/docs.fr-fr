---
title: Événement ETW d'exception Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: 80faf6e607755ee79c7ec17f2d7d3d5bdce822b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716050"
---
# <a name="exception-thrown_v1-etw-event"></a>Événement ETW d'exception Thrown_V1
Cet événement capture des informations sur les exceptions levées.  
  
 Le tableau suivant affiche le mot clé sous lequel l’événement est déclenché, ainsi que le niveau de l’événement. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Avertissement (2)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Event|ID de l'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Une exception managée est levée.|  
  
 Le tableau suivant affiche des données liées aux événements.  
  
|Nom de champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Type d'exception|win:UnicodeString|Type de l’exception, par exemple `System.NullReferenceException`.|  
|Message d’exception|win:UnicodeString|Message d’exception réel.|  
|EIPCodeThrow|win:Pointer|Pointeur d’instruction où l’exception s’est produite.|  
|ExceptionHR|win:UInt32|Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).|  
|ExceptionFlags|win:UInt16|0x01 : HasInnerException (consultez [Événements ETW du CLR](clr-etw-events.md) dans la documentation Visual Basic).<br /><br /> 0x02 : IsNestedException.<br /><br /> 0x04 : IsRethrownException.<br /><br /> 0x08 : IsCorruptedStateException (indique que l’état du processus est endommagé ; consultez [gestion des exceptions d’état endommagé](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).<br /><br /> 0x10 : IsCLSCompliant (une exception qui dérive d’<xref:System.Exception> est conforme CLS ; sinon elle n’est pas conforme CLS).|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](clr-etw-events.md)
