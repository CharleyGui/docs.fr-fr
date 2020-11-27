---
title: Assistant Débogage managé pInvokeLog
description: Comprenez l’Assistant Débogage managé (MDA) pInvokeLog, qui est activé pour chaque signature d’appel de code non managé unique utilisée pendant l’exécution dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: b8cb4805663a2b28a133f98503730199af695c4f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271458"
---
# <a name="pinvokelog-mda"></a>Assistant Débogage managé pInvokeLog

L’Assistant Débogage managé (MDA) `pInvokeLog` est activé pour chaque signature d’appel de code non managé unique utilisée pendant l’exécution.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  

 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Output  

 Message indiquant la signature d’appel de code non managé utilisée lors de l’exécution.  
  
## <a name="configuration"></a>Configuration  

 Chaque élément de correspondance filtre les fichiers .dll en fonction des appels de code non managé effectués.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Diagnostic d'erreurs avec les Assistants de débogage managés](diagnosing-errors-with-managed-debugging-assistants.md)
- [Consommation de fonctions DLL non managées](../interop/consuming-unmanaged-dll-functions.md)
