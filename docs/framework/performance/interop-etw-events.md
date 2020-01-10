---
title: Événements ETW d'interopérabilité
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
ms.openlocfilehash: 80fd1f7487dbe3925b875e728eaeddac86927ad4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716016"
---
# <a name="interop-etw-events"></a>Événements ETW d'interopérabilité
Les événements d'interopérabilité capturent des informations sur la création et la mise en cache du stub MSIL (Microsoft Intermediate Language).  

## <a name="ilstubgenerated-event"></a>Événement ILStubGenerated

Le tableau suivant montre les mots clés et les niveaux. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Event|ID de l'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|Le stub MSIL a été généré.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom de champ|Type de données|Description|  
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
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Event|ID de l'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|Le cache MSIL a fait l’objet d’un accès.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom de champ|Type de données|Description|  
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
