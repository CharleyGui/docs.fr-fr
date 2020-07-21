---
title: Événements ETW de traçage JIT
description: Comprendre les événements ETW de suivi juste-à-temps (JIT). Ces événements collectent des informations relatives à la réussite ou à l’échec de l’incorporation JIT et des appels tail JIT.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
ms.openlocfilehash: 568fc942cd0e2188c530d2befb6260083757ec72
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474460"
---
# <a name="jit-tracing-etw-events"></a>Événements ETW de traçage JIT
Ces événements collectent des informations sur la réussite ou l'échec de l'incorporation (inlining) juste-à-temps (JIT) et des appels tail JIT.

## <a name="jit-inlining-events"></a>Événements d’incorporation (inlining) JIT

### <a name="methodjitinliningfailed-event"></a>Événement MethodJitInliningFailed
 Le tableau suivant montre les mots clés et les niveaux. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Détaillé (5)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186.|L’incorporation JIT a échoué.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Espace de noms de la méthode en cours de compilation.|  
|MethodBeingCompiledName|win:UnicodeString|Nom de la méthode en cours de compilation.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Signature de la méthode en cours de compilation.|  
|InlinerNamespace|win:UnicodeString|Espace de noms de la méthode pour laquelle le compilateur JIT essaie de générer du code.|  
|InlinerName|win:UnicodeString|Nom de la méthode pour laquelle le compilateur essaie de générer du code. Ce n’est peut-être pas le même que `MethodBeingCompiledName` si le compilateur essaie d'incorporer du code dans `MethodBeingCompiledName` au lieu de générer un appel à `InlinerName`.|  
|InlinerNameSignature|win:UnicodeString|Signature de l’incorporateur.|  
|InlineeNamespace|win:UnicodeString|Espace de noms de l’inlinee.|  
|InlineeName|win:UnicodeString|Méthode que le compilateur essaie d'incorporer (ne pas générer d’appel vers cette méthode).|  
|InlineeNameSignature|win:UnicodeString|Signature de l’inlinee.|  
|FailAlways|win:Boolean|Indication destinée au compilateur JIT signalant que l’incorporation (inlining) échouera toujours pour l’inlinee.|  
|FailReason|win:UnicodeString|INLINE_NEVER signifie qu'une tentative d'incorporation (inlining) précédente a déterminé que l'incorporation ne réussirait jamais pour une autre raison ; sinon, texte de forme libre.|  
|ClrInstanceID|win:UnicodeString|ID unique de l'instance de CLR ou CoreCLR.|  
  
### <a name="methodjitinliningsucceeded-event"></a>Événement MethodJitInliningSucceeded  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Détaillé (5)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|L'incorporation de méthode a réussi.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Espace de noms de la méthode en cours de compilation.|  
|MethodBeingCompiledName|win:UnicodeString|Nom de la méthode en cours de compilation.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Signature de la méthode en cours de compilation.|  
|InlinerNamespace|win:UnicodeString|Espace de noms de la méthode pour laquelle le compilateur JIT essaie de générer du code.|  
|InlinerName|win:UnicodeString|Nom de la méthode pour laquelle le compilateur essaie de générer du code. Ce n’est peut-être pas le même que `MethodBeingCompiledName` si le compilateur essaie d'incorporer du code dans `MethodBeingCompiledName` au lieu de générer un appel à `InlinerName`.|  
|InlinerNameSignature|win:UnicodeString|Signature de l’incorporateur.|  
|InlineeNamespace|win:UnicodeString|Espace de noms de l’inlinee.|  
|InlineeName|win:UnicodeString|Méthode que le compilateur essaie d'incorporer (ne pas générer d’appel vers cette méthode).|  
|InlineeNameSignature|win:UnicodeString|Signature de l’inlinee.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  

## <a name="jit-tail-call-events"></a>Événements d'appel tail JIT  
  
### <a name="methodjittailcallfailed-event"></a>Événement MethodJITTailCallFailed  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Détaillé (5)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|L'appel tail de méthode a échoué.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Espace de noms de la méthode en cours de compilation.|  
|MethodBeingCompiledName|win:UnicodeString|Nom de la méthode en cours de compilation.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Signature de la méthode en cours de compilation.|  
|CallerNamespace|win:UnicodeString|Espace de noms de la méthode pour laquelle le compilateur JIT essaie de générer du code.|  
|CallerName|win:UnicodeString|Nom de la méthode pour laquelle le compilateur essaie de générer du code.|  
|CallerNameSignature|win:UnicodeString|Signature de l’appelant.|  
|CalleeNamespace|win:UnicodeString|Espace de noms de l’appelé.|  
|CalleeName|win:UnicodeString|Méthode pour laquelle le compilateur essaie d'effectuer un appel tail (ne pas générer d'appel vers cette méthode).|  
|CalleeNameSignature|win:UnicodeString|Signature de l’appelé.|  
|TailPrefix|win:Boolean|Préfixe de l'appel tail.|  
|FailReason|win:UnicodeString|Raison pour laquelle l'appel tail a échoué.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
### <a name="methodjittailcallsucceeded-event"></a>Événement MethodJITTailCallSucceeded  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Détaillé (5)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|L'appel tail de méthode a réussi.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Espace de noms de la méthode en cours de compilation.|  
|MethodBeingCompiledName|win:UnicodeString|Nom de la méthode en cours de compilation.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Signature de la méthode en cours de compilation.|  
|CallerNamespace|win:UnicodeString|Espace de noms de la méthode pour laquelle le compilateur JIT essaie de générer du code.|  
|CallerName|win:UnicodeString|Nom de la méthode pour laquelle le compilateur essaie de générer du code.|  
|CallerNameSignature|win:UnicodeString|Signature de l’appelant.|  
|CalleeNamespace|win:UnicodeString|Espace de noms de l’appelé.|  
|CalleeName|win:UnicodeString|Méthode pour laquelle le compilateur essaie d'effectuer un appel tail (ne pas générer d'appel vers cette méthode).|  
|CalleeNameSignature|win:UnicodeString|Signature de l’appelé.|  
|TailPrefix|win:Boolean|Préfixe de l’appel tail.|  
|TailCallType|win:UnicodeString|Type de l’appel tail.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](clr-etw-events.md)
