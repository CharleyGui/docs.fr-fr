---
title: Assistant Débogage managé overlappedFreeError
description: Passez en revue l’Assistant Débogage managé (MDA) overlappedFreeError dans .NET, qui peut activer les violations d’accès ou la corruption du tas récupéré par le garbage collector.
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 1bedb8ad3b9801f0d235371a397c8951ff8723b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254530"
---
# <a name="overlappedfreeerror-mda"></a>Assistant Débogage managé overlappedFreeError

L’Assistant Débogage managé `overlappedFreeError` est activé quand la méthode <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> est appelée avant la fin de l’opération avec chevauchement.  
  
## <a name="symptoms"></a>Symptômes  

 Violations d’accès ou altération du tas de la garbage collection.  
  
## <a name="cause"></a>Cause  

 Une structure avec chevauchement a été libérée avant la fin de l’opération. La fonction qui utilise le pointeur avec chevauchement peut écrire dans la structure ultérieurement, une fois qu’elle a été libérée. Ceci peut entraîner une altération du tas, car un autre objet devrait maintenant occuper cette région.  
  
 Cet Assistant Débogage managé peut ne pas représenter une erreur si l’opération avec chevauchement n’a pas démarré correctement.  
  
## <a name="resolution"></a>Résolution  

 Vérifiez que l’opération d’E/S utilisant la structure avec chevauchement est terminée avant d’appeler la méthode <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29>.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  

 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Output  

 Voici un exemple de sortie pour cet Assistant Débogage managé.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d'erreurs avec les Assistants de débogage managés](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d’interopérabilité](../interop/interop-marshaling.md)
