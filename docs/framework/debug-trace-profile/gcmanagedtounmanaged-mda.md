---
title: Assistant Débogage managé gcManagedToUnmanaged
description: Passez en revue l’Assistant Débogage managé gcManagedToUnmanaged. Cet Assistant Débogage managé peut s’activer en raison d’une garbage collection prématurée pendant la transition vers du code non managé.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
ms.openlocfilehash: 668b06109e59f1239cd2b3e3017aeee1916ce69e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244234"
---
# <a name="gcmanagedtounmanaged-mda"></a>Assistant Débogage managé gcManagedToUnmanaged

L'Assistant Débogage managé (MDA) `gcManagedToUnmanaged` déclenche une opération garbage collection chaque fois qu'un thread effectue la transition du code managé au code non managé.  
  
## <a name="symptoms"></a>Symptômes  

 Un composant utilisateur non managé lève une violation d'accès lors de la tentative d'utilisation d'un objet managé qui avait été exposé à COM. L’objet COM semble avoir été libéré. La violation d'accès est non déterministe.  
  
## <a name="cause"></a>Cause  

 Si un composant non managé n'effectue pas correctement le décompte de références d'un objet COM managé, le runtime peut collecter un objet managé exposé à COM lorsque le composant non managé détient encore une référence à l'objet. Le runtime appelle <xref:System.Runtime.InteropServices.Marshal.Release%2A> pendant les opérations garbage collection. Par conséquent, si le composant utilisateur a recours à l’objet avant l’opération garbage collection, il n’aura pas encore été collecté. Cela explique le non-déterminisme.  
  
## <a name="resolution"></a>Résolution  

 L’activation de cet assistant réduit le laps de temps entre le moment où l’objet peut participer à une collection et le moment où <xref:System.Runtime.InteropServices.Marshal.Release%2A> est appelé, ce qui facilite la localisation du composant non managé qui tente en premier d’accéder à l’objet récupéré par le garbage collector.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  

 Provoque une opération garbage collection chaque fois qu'un thread effectue la transition du code managé au code non managé.  
  
## <a name="output"></a>Output  

 Cet Assistant Débogage managé ne produit aucune sortie.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d'erreurs avec les Assistants de débogage managés](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d’interopérabilité](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
