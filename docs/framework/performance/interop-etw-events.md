---
title: Événements ETW d'interopérabilité
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5db68cdce0db4f8f4d85e9d1dd03720bf235d865
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974935"
---
# <a name="interop-etw-events"></a>Événements ETW d'interopérabilité
Les événements d'interopérabilité capturent des informations sur la création et la mise en cache du stub MSIL (Microsoft Intermediate Language).  

## <a name="ilstubgenerated-event"></a>Événement ILStubGenerated

Le tableau suivant montre les mots clés et les niveaux. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|Le stub MSIL a été généré.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt16|Identificateur du module|  
|StubMethodID|win:UInt64|Identificateur de la méthode stub|  
|StubFlags|win:UInt64|Indicateurs du stub :<br /><br /> 0x1 – Interopérabilité inversée.<br /><br /> 0x2 – COM Interop<br /><br /> 0x4 – Stub généré par NGen.exe.<br /><br /> 0x8 – Délégué<br /><br /> 0x10 : argument de variable.<br /><br /> 0x20 – Appelé non managé|  
|ManagedInteropMethodToken|win:UInt32|Jeton de la méthode d’interopérabilité managée|  
|ManagedInteropMethodNameSpace|win:UnicodeString|Espace de noms de la méthode d’interopérabilité managée|  
|ManagedInteropMethodName|win:UnicodeString|Nom de la méthode d’interopérabilité managée|  
|ManagedInteropMethodSignature|win:UnicodeString|Signature de la méthode d'interopérabilité managée|  
|NativeMethodSignature|win:UnicodeString|Signature de la méthode native|  
|StubMethodSignature|win:UnicodeString|Signature de la méthode stub|  
|StubMethodILCode|win:UnicodeString|Code MSIL de la méthode stub|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
## <a name="ilstubcachehit-event"></a>Événement ILStubCacheHit  

Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|Le cache MSIL a fait l’objet d’un accès.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt16|Identificateur du module|  
|StubMethodID|win:UInt64|Identificateur de la méthode stub|  
|ManagedInteropMethodToken|win:UInt32|Jeton de la méthode d’interopérabilité managée|  
|ManagedInteropMethodNameSpace|win:UnicodeString|Espace de noms de la méthode d’interopérabilité managée|  
|ManagedInteropMethodName|win:UnicodeString|Nom de la méthode d’interopérabilité managée|  
|ManagedInteropMethodSignature|win:UnicodeString|Signature de la méthode d'interopérabilité managée|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](clr-etw-events.md)
